* EN: Enable -> wenn betätigt -> Reset
* Boot: Wenn beim Starten gedrückt -> Ändern des Boot-Modus (Download / Flashing Mode)
* GPIO: General Purpose Input / Output

## Digital vs Analog

Digital -> nur bestimmte Zustände -> **diskrete Wertemenge**
Analog -> unendlich viele Werte

### Analog zu Digital

3,.6V - 2,675V -> High

Dazwischen (Verbotene Zone) -> zufällig High oder Low

0,825V - -0,3V -> Low

# Output

## Vorwiderstand berechnen
![[Pasted image 20260108084202.png]]
$$R = \frac{U_R}{I_R} = \frac{3,3V - 1,5V}{20mA} = \frac{1,8V}{20mA} = 90 \ohm$$


Bringt eine LED zum leuchten

```cpp
#include <Arduino.h>

#define led 25

void setup() {
	pinMode(led, OUTPUT);
}

void loop() {
	digitalWrite(led, HIGH);
}
```



# Input

```cpp
#include <Arduino.h>

#define input_switch 32
#define output_led 14

void setup() {
	pinMode(input_switch, INPUT);
	pinMode(output_led, OUTPUT);
}

void loop() {
	if (input_switch == HIGH) {
		digitalWrite(output_led, HIGH);
	} else {
		digitalWrite(output_led, LOW);
	}
	delay(200); //in ms
}
```

# LED dimmen durch PWM (Pulsweitenmodulation)

![[Pasted image 20251023081057.png]]
Tastgrad / Duty cycle = $\frac{Impulsdauer}{Periodendauer}$

Auflösung

```cpp
#include <Arduino.h>

#define led 25

void setup() {
	pinMode(led, OUTPUT);
	ledcSetup(0,100,8);
	ledcAttachPin(led, 0);
}

void loop() {
	for(int i = 0; i <= 10; i++) {
		ledcWrite(0, i*25);
		delay(500);
	}

	for(int i = 10; i >= 0; i--) {
		ledcWrite(0, i*25);
		delay(500);
	}
}
```

# Potentiometer
![[Pasted image 20251106081456.png]]

$R_1 + R_2 = 10k \ohm$ 
Man braucht analog digital converter (wir verwenden 10 bit)

```cpp
#include <Arduino.h>
void setup() {
	Serial.begin(9600) //lässt prints zu
	pinMode(31, INPUT);
}

void loop() {
	Serial.println("DEBUG!")
	analogRead(31);
}
```
Das Fertige Programm ist wie folgt.
```cpp
#include <Arduino.h>

#define input_pot 32
#define output_diode 17

void setup() {
	Serial.begin(9600);
	
	pinMode(output_diode, OUTPUT);
	pinMode(input_pot, INPUT);
	
	ledcSetup(0,100,10);
	ledcAttachPin(output_diode, 0);
}

void loop() {
	Serial.printf("%d\n", analogRead(input_pot));
	ledcWrite(0,analogRead(input_pot) / 4); // von 12b -> 10b
	delay(200);
}
```

# Timer

Fertiges Programm (lässt led im Sekundentakt ein und aus gehen)
```cpp
#include <Arduino.h>

#define output_diode 17

hw_timer_t *timer = NULL;

bool ledShouldGlow = false;

// Interrupt-Service-Routine (ISR)
void onTimer() {
	ledShouldGlow = !ledShouldGlow;
	digitalWrite(output_diode, ledShouldGlow);
}

void setup() {
	pinMode(output_diode, OUTPUT);
	timer = timerBegin(0,80,true);
	timerAttachInterrupt(timer, &onTimer, true);
	timerAlarmWrite(timer, 1000000, true); // entspricht 1s
	timerAlarmEnable(timer);
}

void loop() {}
```

# Rising- und Falling-Edge Erkennung

Für rising-edge
```cpp
#include <Arduino.h>

#define input_pin 17

int counted_rising_edges = 0;
int old_counted_rising_edges = 0;

void IRAM_ATTR onRisingEdge() {
	counted_rising_edges++;
}

void setup() {
	Serial.begin(9600);
	pinMode(input_pin, INPUT_PULLDOWN);
	attachInterrupt(digitalPinToInterrupt(input_pin), &onRisingEdge, RISING);
}

void loop() {
	if (counted_rising_edges != old_counted_rising_edges) {
		old_counted_rising_edges = counted_rising_edges;
		Serial.printf("Times the ESP edged: [%d]\n", counted_rising_edges);
	}
}
```


Für falling-edge

# Kommunikation via Wifi

Zuerst braucht der ESP eine WLAN-Verbindung, welche in diesem Fall kein Passwort braucht, da das WLAN `HTLIoT` die MAC-Adresse der Geräte kennt und diese sich so "authentifizieren".
```cpp
#include <Arduino.h>
#include <WiFi.h>

#define SSID "HTLIoT"
#define PSK "hollabrunn" //Preshared key

void setup() {
	WiFi.setHostname("ESP-IT-07");
	WiFi.begin(SSID,PSK);
	while (!WiFi.isConnected()) {
		delay(200);
	}
	WiFi.localIP();
}
```


Der MikroController startet hier einen Webserver.
```cpp
```
Dieser Webserver hat Schnittpunkte welche wenn sie aufgerufen werden, eine Funktion ausführen. Durch diese Funktionen kann eine LED ein und ausgeschaltet werden.
```
```


```cpp
#include <Arduino.h>
#include <WiFi.h>
#include <WebServer.h>
#include <HTTPClient.h>

// IO
#define OUTPUT_PIN 17

// Wifi
#define SSID "HTLIoT"
#define PSK "hollabrunn" //Preshared key


String PAIRED_ESP_URL = "http://172.168.10.10";
String TURN_ON_PATH = "/turn/on";
String TURN_OFF_PATH = "/turn/off";

WebServer ws(80);
HTTPClient client;

void turnOn();
void turnOff();

void setup() {
	Serial.begin(9600);

	pinMode(OUTPUT_PIN, OUTPUT);

	Serial.print("Begin connecting to Wifi\n");
	WiFi.setHostname("ESP-IT-07");
	WiFi.begin(SSID,PSK);
	while (!WiFi.isConnected()) {
		delay(200);
		Serial.print(".");
	}
	Serial.print(WiFi.localIP());
	Serial.print("Starting Webserver\n");
	ws.on(TURN_ON_PATH, turnOn); //wenn /turn/on aufgerufen wird für Funktion "turnOn" aus
	ws.on(TURN_OFF_PATH, turnOff);
	ws.begin();

	//Begin client
	client.begin((PAIRED_ESP_URL + TURN_ON_PATH).c_str());
}

void loop() {
	ws.handleClient();
	//client.setURL("url string");
	//client.GET();
	delay(200);
}

void turnOn() {
	digitalWrite(OUTPUT_PIN, HIGH);
	ws.send(200, "text/json", "{\"status\": \"On\"}");
}

void turnOff() {
	digitalWrite(OUTPUT_PIN, LOW);
	ws.send(200, "text/json", "{\"status\": \"Off\"}");
}
```

# Kommunikation über Wifi mit MQTT Protokoll

Alle Schalter sollen alle Boards ein und ausschalten können.

```Bash
mosquitto_pub --cafile ~/Downloads/ca.cer -t 4xhits2526/test -m "on" -u 4xhits2526 -P 4xhits2526 -h mqtt.htl-hl.ac.at
```

Im Projekt muss die library `PubSubClient` eingebunden werden

```cpp
#include <Arduino.h>
#include <PubSubClient.h>
#include <WiFiClientSecure.h>

// IO
#define OUTPUT_PIN 17
#define INPUT_PIN 32

// Wifi
#define SSID "HTLIoT"
#define PSK "hollabrunn" //Preshared key

//MQTT
#define TOPIC "4xhits2526/test"
#define LED_ON_PAYLOAD "on"
#define LED_OFF_PAYLOAD "off"

const char* cacert = "";

void mqtt_callback(char* topic, byte* payload, unsigned int length);
void ethClient();

WiFiClientSecure wifi_client;
PubSubClient mqtt_client(wifi_client);

bool lastButtonState;

void setup() {
	Serial.begin(9600);

	pinMode(INPUT_PIN, INPUT_PULLDOWN);
	pinMode(OUTPUT_PIN, OUTPUT);

	lastButtonState = digitalRead(INPUT_PIN);

	WiFi.begin(SSID, PSK);
	while (!WiFi.isConnected()) {
		delay(200);
	}
	Serial.printf("[DEBUG] IP-address: %s\n", WiFi.localIP());
	wifi_client.setCACert(cacert);

	mqtt_client.setServer("mqtt.htl-hl.ac.at", 8883); //domain, port

	mqtt_client.setCallback(mqtt_callback);


	mqtt_client.connect("Lichtenwallner_esp", "4xhits2526", "4xhits2526"); //id, user, password
	Serial.println("Connecting to mqtt");
	while (!mqtt_client.connected()) {
		delay(200);
		Serial.print(".");
	}
	Serial.println("Done!");
	
	mqtt_client.subscribe(TOPIC);
}

void loop() {
	mqtt_client.loop();
	if (digitalRead(INPUT_PIN) != lastButtonState) {
		Serial.println("\nButton changed");
		lastButtonState = !lastButtonState;
		if (lastButtonState) {
			// Button is on
			mqtt_client.publish(TOPIC, LED_ON_PAYLOAD);
			Serial.println("Published on");
		} else {
			// Button is off
			mqtt_client.publish(TOPIC, LED_OFF_PAYLOAD);
			Serial.println("Published off");
		}
	}
	delay(200);
}

void mqtt_callback(char* topic, byte* payload, unsigned int length) {
	char* payloadString = (char*) payload;
	Serial.printf("\nReceived on [%s]:\n%s\n", topic, payloadString);

	if (length == 2 && memcmp(payloadString, LED_ON_PAYLOAD, length)) {
		digitalWrite(OUTPUT_PIN, HIGH);
	} else if (length == 3 && memcmp(payloadString, LED_OFF_PAYLOAD, length)) {
		digitalWrite(OUTPUT_PIN, LOW);
	}
}
```

# OLED Display

![[Pasted image 20260115094953.png]]

Jeder Slave hat eine 7bit (10bit) Adresse

I2C

Wir wollen:
* Am Anfang `Hello` anzeigen
* ADC
* U: Auf 2 dezimalen

```cpp
#include <Arduino.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define OLED_Address 0x3C       // Change to 0x3C if needed

#define OUTPUT_PIN 17          // Not used yet
#define INPUT_PIN 34               // Potentiometer input

#define Screen_width 128
#define Screen_height 64
#define OLED_RESET -1          // ESP32 usually doesn't need reset pin

#define ADC_RESOLUTION 10
#define ADC_MAX_VALUE 1023.0
#define VREF 3.3               // ESP32 reference voltage

int graphData[Screen_width];
int graphDataStart = 0;
int currentGraphDataIndex = 0;

void pushGraphData(int data) {
    graphData[currentGraphDataIndex] = data;
    if(currentGraphDataIndex == Screen_width - 1) {
        currentGraphDataIndex = 0;
    } else {
        currentGraphDataIndex += 1;
    }
    if (currentGraphDataIndex <= graphDataStart) {
        if(graphDataStart == Screen_width - 1) {
            graphDataStart = 0;
        } else {
            graphDataStart += 1;
        }
    }
}

// chars sind 7p hoch
Adafruit_SSD1306 display(Screen_width, Screen_height, &Wire, OLED_RESET);

void setup() {
  Serial.begin(115200);

  for(int i = 0; i < Screen_width; i++) {
    graphData[i] = 0;
  }

  // Set ADC resolution to 10-bit
  analogReadResolution(ADC_RESOLUTION);

  pinMode(INPUT_PIN, INPUT);

  // Initialize I2C
  Wire.begin();

  // Initialize OLED
  if (!display.begin(SSD1306_SWITCHCAPVCC, OLED_Address)) {
    Serial.println("OLED init failed");
    while (true);
  }

  display.clearDisplay();
  display.setTextColor(SSD1306_WHITE);
  display.setTextSize(1);
}

void loop() {
  // Read potentiometer
  int adcValue = analogRead(INPUT_PIN);

  pushGraphData(adcValue);

  // Convert to voltage
  float voltage = (adcValue / ADC_MAX_VALUE) * VREF;

  // Print to Serial Monitor
  Serial.print("ADC: ");
  Serial.print(adcValue);
  Serial.print("  Voltage: ");
  Serial.println(voltage, 3);

  // Display on OLED
  display.clearDisplay();

  display.setCursor(0, 0);
  display.println("Potentiometer");

  //display.setCursor(0, 20);
  //display.print("ADC Value: ");
  //display.println(adcValue);

  display.setCursor(0, 15);
  display.print("Voltage: ");
  display.print(voltage, 3);
  display.println(" V");

  int xPos = 0;
  for(int i = graphDataStart; i != currentGraphDataIndex; xPos++) {
    int yPos = Screen_height - ((graphData[i] / ADC_MAX_VALUE) * 40) - 1;

    //display.setCursor(xPos, yPos);
    display.drawPixel(xPos, yPos, SSD1306_WHITE);

    if(i == Screen_width - 1) {
        i = 0;
    } else {
        i += 1;
    }
  }

  display.display();

  delay(200);
}
```

# Temperatursensor

DS18B20
Externe hardware für Mikrocontroller
Verwendete Protokoll heißt 1-Wire, weil eine Datenleitung. Ist auf einem Bus, geht auf weite Distanzen. Hat normalerweise 3 Kontakte (Datenleitung, Versorgung & Masse) geht aber auch mit 2 Kontakten wo Datenleitung auch für die Stromversorgung verwendet werden kann.

[Datenblatt von DS18B20](https://www.analog.com/media/en/technical-documentation/data-sheets/DS18B20.pdf)
[Nerdtut. für den Sensor](https://randomnerdtutorials.com/esp32-ds18b20-temperature-arduino-ide/)


![[Pasted image 20260212082044.png]]
Dadurch dass das gerät auf einem Bus ist hat es eine Adresse, diese ist 8 Byte lang

```cpp
  /*********
  Rui Santos
  Complete project details at https://RandomNerdTutorials.com  
*********/

#include <OneWire.h>
#include <DallasTemperature.h>
#include <Arduino.h>
#include <WiFi.h>
#include <WebServer.h>
#include <HTTPClient.h>
#include <bits/stdc++.h>
using namespace std;

// Wifi
#define SSID "HTLIoT"
#define PSK "hollabrunn" //Preshared key

WebServer webserver(80);
HTTPClient client;

// GPIO where the DS18B20 is connected to
const int oneWireBus = 4;     

// Setup a oneWire instance to communicate with any OneWire devices
OneWire oneWire(oneWireBus);

// Pass our oneWire reference to Dallas Temperature sensor 
DallasTemperature sensors(&oneWire);

void getTemp();

void setup() {
  // Start the Serial Monitor
  Serial.begin(9600);
  // Start the DS18B20 sensor
  sensors.begin();

  //WiFi
  Serial.print("Begin connecting to Wifi\n");
	WiFi.setHostname("ESP-IT-07");
	WiFi.begin(SSID,PSK);
	while (!WiFi.isConnected()) {
		delay(200);
	}
	Serial.printf("[DEBUG] IP-address: %s\n", "");
  Serial.println(WiFi.localIP());
	Serial.print("Starting Webserver\n");
	webserver.on("/", getTemp); //wenn /turn/on aufgerufen wird für Funktion "turnOn" aus
	webserver.begin();
}

void loop() {
  webserver.handleClient();
  Serial.println(WiFi.localIP());
	delay(200);
}

void getTemp() {
  sensors.requestTemperatures(); 
  float temperatureC = sensors.getTempCByIndex(0);
  float temperatureF = sensors.getTempFByIndex(0);
  Serial.print(temperatureC);
  Serial.println("ºC");
  Serial.print(temperatureF);
  Serial.println("ºF");

  //"{\"temperature\":" + to_string(temperatureC) + "}"
  String output = "{\"temperature\":";
  output.concat(String(temperatureC));
  output.concat("}");

  webserver.send(200, "text/json", output);
}
```

# Timer

Durch Interrupts.

![[Pasted image 20260219081131.png]]

[ntp client tut](https://randomnerdtutorials.com/esp32-date-time-ntp-client-server-arduino/)
[display tut](https://randomnerdtutorials.com/esp32-ssd1306-oled-display-arduino-ide/)

```cpp
//#include <OneWire.h>
//#include <DallasTemperature.h>
#include <Arduino.h>
#include <WiFi.h>
//#include <WebServer.h>
#include <HTTPClient.h>
#include <bits/stdc++.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#include "time.h"
using namespace std;

// About
#define PROGRAM_NAME "main.cpp"
#define PROGRAM_VERSION "Alpha 0.4"

//Timer stuff
#define ROUND_PIN 26
#define START_STOP_PIN 27
#define RESET_PIN 25

hw_timer_t *timer = NULL;

int milliseconds = 0;
int seconds      = 0;
int minutes      = 0;
int hours        = 0;

bool shouldPauseTimer = false;
bool shouldResetTimer = false;
bool last_round_state = false;
bool last_start_stop_state = false;
bool last_reset_state = false;

int timer_start_timestamp = 0;
int timer_start_mill_secs = 0;
int timer_rounds[255];


// Wifi
#define SSID "HTLIoT"
#define PSK "hollabrunn" //Preshared key

// ntp time
const char* ntpServer = "time.metrologie.at";
const long  gmtOffset_sec = 3600;
const int   daylightOffset_sec = 0;

//WebServer webserver(80);
//HTTPClient client;

// screen
#define OLED_Address 0x3C 
#define Screen_width 128
#define Screen_height 64
#define OLED_RESET -1 

Adafruit_SSD1306 display(Screen_width, Screen_height, &Wire, OLED_RESET);

void getIndexPage();

void onTimer() {
  if (shouldPauseTimer) {
    return;
  }

  milliseconds++;
  if (milliseconds >= 1000) {
    milliseconds = 0;
    seconds++;
  }
  if (seconds >= 60) {
    seconds = 0;
    minutes++;
  }
  if (minutes >= 60) {
    minutes = 0;
    hours++;
  }
}

void setup() {
  // Start the Serial Monitor
  Serial.begin(9600);

  // Initialize I2C
  Wire.begin();

  // Initialize OLED
  if (!display.begin(SSD1306_SWITCHCAPVCC, OLED_Address)) {
    Serial.println("OLED init failed");
    while (true);
  }

  display.clearDisplay();
  display.setTextColor(SSD1306_WHITE);
  display.setTextSize(1);

  // Timer Controlls
  pinMode(ROUND_PIN,      INPUT_PULLDOWN);
  pinMode(START_STOP_PIN, INPUT_PULLDOWN);
  pinMode(RESET_PIN,      INPUT_PULLDOWN);

  last_round_state      = digitalRead(ROUND_PIN);
  last_start_stop_state = digitalRead(START_STOP_PIN);
  last_reset_state      = digitalRead(RESET_PIN);

  //Timer
  timer = timerBegin(0,80,true);
	timerAttachInterrupt(timer, &onTimer, true);
	timerAlarmWrite(timer, 1000, true); //1.000.000 entspricht 1s
	timerAlarmEnable(timer);

  //init rounds
  for (int i = 0; i < sizeof(timer_rounds) / sizeof(timer_rounds[0]); i++) {
    timer_rounds[i] = -1;
  }

  //WiFi
  Serial.print("Begin connecting to Wifi\n");
	WiFi.setHostname("ESP-IT-07");
	WiFi.begin(SSID,PSK);
	while (!WiFi.isConnected()) {
		delay(200);
	}

  configTime(gmtOffset_sec, daylightOffset_sec, ntpServer);

  struct tm timeinfo;
  while (!getLocalTime(&timeinfo)) {
    Serial.print(".");
    delay(500);
  }

  WiFi.disconnect(true);
  WiFi.mode(WIFI_OFF);
}

void loop() {
  struct tm timeinfo;
  if(!getLocalTime(&timeinfo)){
    Serial.println("Failed to obtain time");
  }

  if(digitalRead(ROUND_PIN) != last_round_state) {
    last_round_state = !last_round_state;
    Serial.printf("%d:%d:%d:%d\n", hours, minutes, seconds, milliseconds);
  }
  if(digitalRead(START_STOP_PIN) != last_start_stop_state) {
    last_start_stop_state = !last_start_stop_state;
    shouldPauseTimer = !shouldPauseTimer;
    // REset
  }
  if(digitalRead(RESET_PIN) != last_reset_state) {
    last_reset_state = !last_reset_state;
    shouldResetTimer = !shouldResetTimer;
    // REset
  }

  /*if(last_start_stop_state) {
    timer_start_timestamp = timestamp * 1000 + mill_secs;
  }*/

  if (shouldResetTimer) {
    milliseconds = 0;
    seconds = 0;
    minutes = 0;
    hours = 0;
  }

  display.clearDisplay();

  display.setCursor(0, 0);
  display.print(PROGRAM_NAME);
  display.print(": ");
  display.println(PROGRAM_VERSION);

  display.setCursor(0, 20);

  display.println(&timeinfo, "%H:%M:%S");

  display.setCursor(0, 35);

  display.print(hours);
  display.print(":");
  display.print(minutes);
  display.print(":");
  display.print(seconds);
  display.print(":");
  display.println(milliseconds);

  display.setCursor(0, 50);

  if (shouldPauseTimer) {
    display.print("P");
  } else {
    display.print(" ");
  }
  if (shouldResetTimer) {
    display.print("R");
  } else {
    display.print(" ");
  }

  display.display();

  shouldResetTimer = false;

  //webserver.handleClient();
  //Serial.println(WiFi.localIP());
	delay(200);
}
```

# Tasmota
Ist besonders gut, wenn man ein WLAN-Gerät kauft, welches "schlechte" Firmware hat. Hier kann diese Firmware überschrieben werden um, z.B. nicht an die Cloudlösungen des Herstellers gebunden zu sein.

klone dieses [Repo](https://github.com/arendst/Tasmota). Danach füge den Ordner in VsCode hinzu in dem man `File` -> `Add Folder to Workspace` drückt und den geklonten Ordner auswählst.
![[Pasted image 20260305092148.png|245]]

in der unteren Leiste wähle dieses Symbol aus:
![[Pasted image 20260305092332.png]]
Es wird eine Suche geöffnet. In dieser sucht und wählt man `tasmota32`
![[Pasted image 20260305092507.png]]
Jetzt wird das Projekt kompiliert. und auf den ESP32 gespielt. Wenn ein kompiliertes Projekt heruntergeladen wurde, kann man den Schritten dieses [Tutorials](https://docs.espressif.com/projects/esptool/en/latest/esp32/) folgen.
Nach dem das Programm auf dem ESP32 ist wird dieser ein WLAN öffnen. Mit diesem muss man sich verbinden. Man selbst bekommt eine IP-Adresse wie: `x.x.x.2` in einem browser gibt nun die Adresse des Boards ein: `x.x.x.1`. Es wird eine Oberfläche erscheinen.

Unter `Tools -> Console` um die LED ein und aus zu schalten.
```
LedPower1 1
LedPower1 0
```

Solche Befehle können auch über Webrequests gegeben werden
```
http://172.18.40.72/cm?cmnd=LedPower%20Toggle
http://172.18.40.72/cm?cmnd=LedPower%201
http://172.18.40.72/cm?cmnd=LedPower%200
```
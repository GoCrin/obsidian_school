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
```cpp
// Interrupt-Service-Routine (ISR)
void IRAM_ATTR onTimer() {
	if (timerFlag == false) {
		timerFlag = true;
	}
}

//Setup...
timer = timerBegin(1000000); // Zeit in mikrosekunden
timerAttachInterrupt(timer, &onTimer, true);
timerAlarm(timer, 50000, true);
```

Fertiges Programm (lässt led im Sekundentakt ein und aus gehen)
```cpp
#include <Arduino.h>

#define output_diode 17

hw_timer_t *timer = NULL;

bool ledShouldGlow = false;

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

const char* cacert = "-----BEGIN CERTIFICATE-----\n"\
"MIIG1TCCBL2gAwIBAgIQbFWr29AHksedBwzYEZ7WvzANBgkqhkiG9w0BAQwFADCB\n"\
"iDELMAkGA1UEBhMCVVMxEzARBgNVBAgTCk5ldyBKZXJzZXkxFDASBgNVBAcTC0pl\n"\
"cnNleSBDaXR5MR4wHAYDVQQKExVUaGUgVVNFUlRSVVNUIE5ldHdvcmsxLjAsBgNV\n"\
"BAMTJVVTRVJUcnVzdCBSU0EgQ2VydGlmaWNhdGlvbiBBdXRob3JpdHkwHhcNMjAw\n"\
"MTMwMDAwMDAwWhcNMzAwMTI5MjM1OTU5WjBLMQswCQYDVQQGEwJBVDEQMA4GA1UE\n"\
"ChMHWmVyb1NTTDEqMCgGA1UEAxMhWmVyb1NTTCBSU0EgRG9tYWluIFNlY3VyZSBT\n"\
"aXRlIENBMIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAhmlzfqO1Mdgj\n"\
"4W3dpBPTVBX1AuvcAyG1fl0dUnw/MeueCWzRWTheZ35LVo91kLI3DDVaZKW+TBAs\n"\
"JBjEbYmMwcWSTWYCg5334SF0+ctDAsFxsX+rTDh9kSrG/4mp6OShubLaEIUJiZo4\n"\
"t873TuSd0Wj5DWt3DtpAG8T35l/v+xrN8ub8PSSoX5Vkgw+jWf4KQtNvUFLDq8mF\n"\
"WhUnPL6jHAADXpvs4lTNYwOtx9yQtbpxwSt7QJY1+ICrmRJB6BuKRt/jfDJF9Jsc\n"\
"RQVlHIxQdKAJl7oaVnXgDkqtk2qddd3kCDXd74gv813G91z7CjsGyJ93oJIlNS3U\n"\
"gFbD6V54JMgZ3rSmotYbz98oZxX7MKbtCm1aJ/q+hTv2YK1yMxrnfcieKmOYBbFD\n"\
"hnW5O6RMA703dBK92j6XRN2EttLkQuujZgy+jXRKtaWMIlkNkWJmOiHmErQngHvt\n"\
"iNkIcjJumq1ddFX4iaTI40a6zgvIBtxFeDs2RfcaH73er7ctNUUqgQT5rFgJhMmF\n"\
"x76rQgB5OZUkodb5k2ex7P+Gu4J86bS15094UuYcV09hVeknmTh5Ex9CBKipLS2W\n"\
"2wKBakf+aVYnNCU6S0nASqt2xrZpGC1v7v6DhuepyyJtn3qSV2PoBiU5Sql+aARp\n"\
"wUibQMGm44gjyNDqDlVp+ShLQlUH9x8CAwEAAaOCAXUwggFxMB8GA1UdIwQYMBaA\n"\
"FFN5v1qqK0rPVIDh2JvAnfKyA2bLMB0GA1UdDgQWBBTI2XhootkZaNU9ct5fCj7c\n"\
"tYaGpjAOBgNVHQ8BAf8EBAMCAYYwEgYDVR0TAQH/BAgwBgEB/wIBADAdBgNVHSUE\n"\
"FjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwIgYDVR0gBBswGTANBgsrBgEEAbIxAQIC\n"\
"TjAIBgZngQwBAgEwUAYDVR0fBEkwRzBFoEOgQYY/aHR0cDovL2NybC51c2VydHJ1\n"\
"c3QuY29tL1VTRVJUcnVzdFJTQUNlcnRpZmljYXRpb25BdXRob3JpdHkuY3JsMHYG\n"\
"CCsGAQUFBwEBBGowaDA/BggrBgEFBQcwAoYzaHR0cDovL2NydC51c2VydHJ1c3Qu\n"\
"Y29tL1VTRVJUcnVzdFJTQUFkZFRydXN0Q0EuY3J0MCUGCCsGAQUFBzABhhlodHRw\n"\
"Oi8vb2NzcC51c2VydHJ1c3QuY29tMA0GCSqGSIb3DQEBDAUAA4ICAQAVDwoIzQDV\n"\
"ercT0eYqZjBNJ8VNWwVFlQOtZERqn5iWnEVaLZZdzxlbvz2Fx0ExUNuUEgYkIVM4\n"\
"YocKkCQ7hO5noicoq/DrEYH5IuNcuW1I8JJZ9DLuB1fYvIHlZ2JG46iNbVKA3ygA\n"\
"Ez86RvDQlt2C494qqPVItRjrz9YlJEGT0DrttyApq0YLFDzf+Z1pkMhh7c+7fXeJ\n"\
"qmIhfJpduKc8HEQkYQQShen426S3H0JrIAbKcBCiyYFuOhfyvuwVCFDfFvrjADjd\n"\
"4jX1uQXd161IyFRbm89s2Oj5oU1wDYz5sx+hoCuh6lSs+/uPuWomIq3y1GDFNafW\n"\
"+LsHBU16lQo5Q2yh25laQsKRgyPmMpHJ98edm6y2sHUabASmRHxvGiuwwE25aDU0\n"\
"2SAeepyImJ2CzB80YG7WxlynHqNhpE7xfC7PzQlLgmfEHdU+tHFeQazRQnrFkW2W\n"\
"kqRGIq7cKRnyypvjPMkjeiV9lRdAM9fSJvsB3svUuu1coIG1xxI1yegoGM4r5QP4\n"\
"RGIVvYaiI76C0djoSbQ/dkIUUXQuB8AL5jyH34g3BZaaXyvpmnV4ilppMXVAnAYG\n"\
"ON51WhJ6W0xNdNJwzYASZYH+tmCWI+N60Gv2NNMGHwMZ7e9bXgzUCZH5FaBFDGR5\n"\
"S9VWqHB73Q+OyIVvIbKYcSc2w/aSuFKGSA==\n"\
"-----END CERTIFICATE-----\n"\
"-----BEGIN CERTIFICATE-----\n"\
"MIIFgTCCBGmgAwIBAgIQOXJEOvkit1HX02wQ3TE1lTANBgkqhkiG9w0BAQwFADB7\n"\
"MQswCQYDVQQGEwJHQjEbMBkGA1UECAwSR3JlYXRlciBNYW5jaGVzdGVyMRAwDgYD\n"\
"VQQHDAdTYWxmb3JkMRowGAYDVQQKDBFDb21vZG8gQ0EgTGltaXRlZDEhMB8GA1UE\n"\
"AwwYQUFBIENlcnRpZmljYXRlIFNlcnZpY2VzMB4XDTE5MDMxMjAwMDAwMFoXDTI4\n"\
"MTIzMTIzNTk1OVowgYgxCzAJBgNVBAYTAlVTMRMwEQYDVQQIEwpOZXcgSmVyc2V5\n"\
"MRQwEgYDVQQHEwtKZXJzZXkgQ2l0eTEeMBwGA1UEChMVVGhlIFVTRVJUUlVTVCBO\n"\
"ZXR3b3JrMS4wLAYDVQQDEyVVU0VSVHJ1c3QgUlNBIENlcnRpZmljYXRpb24gQXV0\n"\
"aG9yaXR5MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAgBJlFzYOw9sI\n"\
"s9CsVw127c0n00ytUINh4qogTQktZAnczomfzD2p7PbPwdzx07HWezcoEStH2jnG\n"\
"vDoZtF+mvX2do2NCtnbyqTsrkfjib9DsFiCQCT7i6HTJGLSR1GJk23+jBvGIGGqQ\n"\
"Ijy8/hPwhxR79uQfjtTkUcYRZ0YIUcuGFFQ/vDP+fmyc/xadGL1RjjWmp2bIcmfb\n"\
"IWax1Jt4A8BQOujM8Ny8nkz+rwWWNR9XWrf/zvk9tyy29lTdyOcSOk2uTIq3XJq0\n"\
"tyA9yn8iNK5+O2hmAUTnAU5GU5szYPeUvlM3kHND8zLDU+/bqv50TmnHa4xgk97E\n"\
"xwzf4TKuzJM7UXiVZ4vuPVb+DNBpDxsP8yUmazNt925H+nND5X4OpWaxKXwyhGNV\n"\
"icQNwZNUMBkTrNN9N6frXTpsNVzbQdcS2qlJC9/YgIoJk2KOtWbPJYjNhLixP6Q5\n"\
"D9kCnusSTJV882sFqV4Wg8y4Z+LoE53MW4LTTLPtW//e5XOsIzstAL81VXQJSdhJ\n"\
"WBp/kjbmUZIO8yZ9HE0XvMnsQybQv0FfQKlERPSZ51eHnlAfV1SoPv10Yy+xUGUJ\n"\
"5lhCLkMaTLTwJUdZ+gQek9QmRkpQgbLevni3/GcV4clXhB4PY9bpYrrWX1Uu6lzG\n"\
"KAgEJTm4Diup8kyXHAc/DVL17e8vgg8CAwEAAaOB8jCB7zAfBgNVHSMEGDAWgBSg\n"\
"EQojPpbxB+zirynvgqV/0DCktDAdBgNVHQ4EFgQUU3m/WqorSs9UgOHYm8Cd8rID\n"\
"ZsswDgYDVR0PAQH/BAQDAgGGMA8GA1UdEwEB/wQFMAMBAf8wEQYDVR0gBAowCDAG\n"\
"BgRVHSAAMEMGA1UdHwQ8MDowOKA2oDSGMmh0dHA6Ly9jcmwuY29tb2RvY2EuY29t\n"\
"L0FBQUNlcnRpZmljYXRlU2VydmljZXMuY3JsMDQGCCsGAQUFBwEBBCgwJjAkBggr\n"\
"BgEFBQcwAYYYaHR0cDovL29jc3AuY29tb2RvY2EuY29tMA0GCSqGSIb3DQEBDAUA\n"\
"A4IBAQAYh1HcdCE9nIrgJ7cz0C7M7PDmy14R3iJvm3WOnnL+5Nb+qh+cli3vA0p+\n"\
"rvSNb3I8QzvAP+u431yqqcau8vzY7qN7Q/aGNnwU4M309z/+3ri0ivCRlv79Q2R+\n"\
"/czSAaF9ffgZGclCKxO/WIu6pKJmBHaIkU4MiRTOok3JMrO66BQavHHxW/BBC5gA\n"\
"CiIDEOUMsfnNkjcZ7Tvx5Dq2+UUTJnWvu6rvP3t3O9LEApE9GQDTF1w52z97GA1F\n"\
"zZOFli9d31kWTz9RvdVFGD/tSo7oBmF0Ixa1DVBzJ0RHfxBdiSprhTEUxOipakyA\n"\
"vGp4z7h/jnZymQyd/teRCBaho1+V\n"\
"-----END CERTIFICATE-----\n"\
"-----BEGIN CERTIFICATE-----\n"\
"MIIEMjCCAxqgAwIBAgIBATANBgkqhkiG9w0BAQUFADB7MQswCQYDVQQGEwJHQjEb\n"\
"MBkGA1UECAwSR3JlYXRlciBNYW5jaGVzdGVyMRAwDgYDVQQHDAdTYWxmb3JkMRow\n"\
"GAYDVQQKDBFDb21vZG8gQ0EgTGltaXRlZDEhMB8GA1UEAwwYQUFBIENlcnRpZmlj\n"\
"YXRlIFNlcnZpY2VzMB4XDTA0MDEwMTAwMDAwMFoXDTI4MTIzMTIzNTk1OVowezEL\n"\
"MAkGA1UEBhMCR0IxGzAZBgNVBAgMEkdyZWF0ZXIgTWFuY2hlc3RlcjEQMA4GA1UE\n"\
"BwwHU2FsZm9yZDEaMBgGA1UECgwRQ29tb2RvIENBIExpbWl0ZWQxITAfBgNVBAMM\n"\
"GEFBQSBDZXJ0aWZpY2F0ZSBTZXJ2aWNlczCCASIwDQYJKoZIhvcNAQEBBQADggEP\n"\
"ADCCAQoCggEBAL5AnfRu4ep2hxxNRUSOvkbIgwadwSr+GB+O5AL686tdUIoWMQua\n"\
"BtDFcCLNSS1UY8y2bmhGC1Pqy0wkwLxyTurxFa70VJoSCsN6sjNg4tqJVfMiWPPe\n"\
"3M/vg4aijJRPn2jymJBGhCfHdr/jzDUsi14HZGWCwEiwqJH5YZ92IFCokcdmtet4\n"\
"YgNW8IoaE+oxox6gmf049vYnMlhvB/VruPsUK6+3qszWY19zjNoFmag4qMsXeDZR\n"\
"rOme9Hg6jc8P2ULimAyrL58OAd7vn5lJ8S3frHRNG5i1R8XlKdH5kBjHYpy+g8cm\n"\
"ez6KJcfA3Z3mNWgQIJ2P2N7Sw4ScDV7oL8kCAwEAAaOBwDCBvTAdBgNVHQ4EFgQU\n"\
"oBEKIz6W8Qfs4q8p74Klf9AwpLQwDgYDVR0PAQH/BAQDAgEGMA8GA1UdEwEB/wQF\n"\
"MAMBAf8wewYDVR0fBHQwcjA4oDagNIYyaHR0cDovL2NybC5jb21vZG9jYS5jb20v\n"\
"QUFBQ2VydGlmaWNhdGVTZXJ2aWNlcy5jcmwwNqA0oDKGMGh0dHA6Ly9jcmwuY29t\n"\
"b2RvLm5ldC9BQUFDZXJ0aWZpY2F0ZVNlcnZpY2VzLmNybDANBgkqhkiG9w0BAQUF\n"\
"AAOCAQEACFb8AvCb6P+k+tZ7xkSAzk/ExfYAWMymtrwUSWgEdujm7l3sAg9g1o1Q\n"\
"GE8mTgHj5rCl7r+8dFRBv/38ErjHT1r0iWAFf2C3BUrz9vHCv8S5dIa2LX1rzNLz\n"\
"Rt0vxuBqw8M0Ayx9lt1awg6nCpnBBYurDC/zXDrPbDdVCYfeU0BsWO/8tqtlbgT2\n"\
"G9w84FoVxp7Z8VlIMCFlA2zs6SFz7JsDoeA3raAVGI/6ugLOpyypEBMs1OUIJqsi\n"\
"l2D4kF501KKaU73yqWjgom7C12yxow+ev+to51byrvLjKzg6CYG1a4XXvi3tPxq3\n"\
"smPi9WIsgtRqAEFQ8TmDn5XpNpaYbg==\n"\
"-----END CERTIFICATE-----";

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


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
	timer = timerBegin(0,80,true); // Zeit in mikrosekunden
	timerAttachInterrupt(timer, &onTimer, true);
	timerAlarmWrite(timer, 1000000, true); // entspricht 1s
	timerAlarmEnable(timer);
}

void loop() {}
```
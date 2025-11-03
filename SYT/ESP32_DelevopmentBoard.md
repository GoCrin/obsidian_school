* EN: Enable -> wenn betätigt -> Reset
* Boot: Wenn beim Starten gedrückt -> Ändern des Boot-Modus (Download / Flashing Mode)
* GPIO: General Purpose Input / Output
* 

## Digital vs Analog

Digital -> nur bestimmte Zustände -> **diskrete Wertemenge**
Analog -> unendlich viele Werte

### Analog zu Digital

3,.6V - 2,675V -> High

Dazwischen (Verbotene Zone) -> zufällig High oder Low

0,825V - -0,3V -> Low

## Diode

# Input

```cpp
void setup() {
	pinMode(32, INPUT);
	pinMode(14, OUTPUT);
}

void loop() {
	if () {
	} else {
	}
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

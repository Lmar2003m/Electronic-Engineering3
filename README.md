# Electronic-Engineering3
### Idea:
Use an LDR to measure light intensity and adjust LED brightness. More light → dimmer LED, less light → brighter LED.

### Components:
* Arduino
* LDR
* 10kΩ resistor
* LED + 220Ω resistor
* Jumper wires

### Wiring:

* 5V → LDR → junction → A0
* From the same junction → 10kΩ resistor → GND
* LED from pin 13 (with resistor) → GND

### Code:

int sensorValue = 0;

void setup() {
  pinMode(A0, INPUT);
  pinMode(13, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  sensorValue = analogRead(A0);
  Serial.print(sensorValue);

  int fade = map(sensorValue, 54, 974, 255, 0);
  Serial.print(fade);
  analogWrite(13, fade);

  delay(100);
}

### Result:
Dark → LED is bright
Bright → LED is dim

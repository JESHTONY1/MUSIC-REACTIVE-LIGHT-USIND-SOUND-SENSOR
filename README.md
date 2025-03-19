int soundPin = A0;
int LEDPins[] = {2, 3, 4, 5, 6, 7, 8, 9};
int numLEDs = 8;
void setup() {
for (int i = 0; i < numLEDs; i++) {
pinMode(LEDPins[i], OUTPUT);
}
Serial.begin(9600);
}
void loop() {
int soundValue = analogRead(soundPin);
Serial.println(soundValue);
int ledCount = map(soundValue, 0, 1023, 0, numLEDs);
for (int i = 0; i < numLEDs; i++) {
if (i < ledCount) {
digitalWrite(LEDPins[i], HIGH);
} else {
digitalWrite(LEDPins[i], LOW);
}
}
delay(50);
}

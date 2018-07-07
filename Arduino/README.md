###### boolean button;
###### int ledPin = 2;
###### int buttonState = 0;         
 
######   void setup() {
######     button = false;
######     pinMode (8, INPUT);
######     pinMode (ledPin, OUTPUT);
######     Serial.begin(9600);
######   }
  
######   void loop() {
######    button = digitalRead(8);
######    if (button) {
######      Serial.write("a");
######    } else {
######      Serial.write("b");
######    }
######    buttonState = digitalRead(8);
######   if (buttonState == HIGH) {
######     digitalWrite(ledPin, HIGH);
######   }
######   else {
######     digitalWrite(ledPin, LOW);
######   }
######  }

```arduino
const int analogInPin = A0;  // Analog input pin that the potentiometer is attached to
const int analogOutPin = 9; // Analog output pin that the LED is attached to

int sensorValue = 0;        // value read from the pot
int outputValue = 0;        // value output to the PWM (analog out)

int Pin9;
int Pin10;
int Pin11;
int Pin12;

void setup() {
  // initialize serial communications at 9600 bps:
  Serial.begin(9600);
  pinMode(analogOutPin, OUTPUT);
}

void loop() {
  // read the analog in value:
  sensorValue = analogRead(analogInPin);            
  // map it to the range of the analog out:
  outputValue = map(sensorValue, 0, 1023, 0, 255);  
  // change the analog out value:
  if (sensorValue < 250) {
    digitalWrite(9, HIGH);
    digitalWrite(10, LOW);
    digitalWrite(11, LOW);
    digitalWrite(12, LOW);
  } if (sensorValue > 251) {
      digitalWrite(9, LOW);
      digitalWrite(10, HIGH);
      digitalWrite(11, LOW);
      digitalWrite(12, LOW);
    } if (sensorValue >501) {
      digitalWrite(9, LOW);
      digitalWrite(10, LOW);
      digitalWrite(11, HIGH);
      digitalWrite(12, LOW);
    } if (sensorValue > 751) {
      digitalWrite(9, LOW);
      digitalWrite(10, LOW);
      digitalWrite(11, LOW);
      digitalWrite(12, HIGH);
    }

  // print the results to the serial monitor:
  Serial.print("sensor = " );                       
  Serial.print(sensorValue);      
  Serial.print("\t output = ");      
  Serial.println(outputValue);   

  // wait 2 milliseconds before the next loop
  // for the analog-to-digital converter to settle
  // after the last reading:
  delay(2);                     
}
```
![PIC](https://raw.githubusercontent.com/Ying7930/week8/master/IMG_1671.JPG)

LDR
- When cover the LDR Pin 9 will grow.  When release, Pin 10 to 12 will grow depends on the lightness that given.
- The highest output is 224, lowest is 1.  For the sensor, highest is 902, lowest is 8.
![PIC](https://raw.githubusercontent.com/Ying7930/week8/master/IMG_1682.JPG)
digital multimeter
- The voltage of the LDR is around 4.97
- For the analog sensor pin the voltage is around 4.94
Switch
- When press, pin 12 will grow.  When release the buttom, pin 9 will grow.
- The heighest output is 255, lowest is 0.  For the sensor, highest is 1023, lowest is 2.
![PIC](https://raw.githubusercontent.com/Ying7930/week8/master/IMG_1683.JPG)
analogRead function to digitalRead
- The sensor only show 0 and 1.

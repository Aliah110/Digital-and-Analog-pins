# Digital-and-Analog-pins

## What does this repository contain?
In this repository, I will show a design for two electronic circuits, the first for a digital sensor and the other for an analog sensor.

- First, let's know what Digital and Analog are :<br>
An analog signal can take on any number of values. A digital signal, on the other hand, has only two values: HIGH and LOW. The Arduino has a built-in analog-to-digital converter (ADC) that measures the value of analog signals. The ADC converts the analog voltage into a digital value. The function used in order to obtain the value of an analog signal is analogRead(pin). This function converts the value of an analog input pin’s voltage and returns a digital value from 0 to 1023, relative to the reference value. Most Arduinos have a reference of 5V, 15V on an Arduino Mega, and 7V on the Arduino Mini and Nano. The pin number is its only parameter.

## Electronic circuit for the light sensor (Analog) :
- Circuit design link in tinkercad :<br> https://www.tinkercad.com/things/1YxhIezTwwL
- What LDR (Light Dependent Resistor) is ? <br>
Is a component that has a (variable) resistance that changes with the light intensity that falls upon it, this allows them to be used in light sensing circuits.
![Exquisite Robo](https://user-images.githubusercontent.com/108204114/182065456-f8927ef5-c140-485e-91da-64b5b7c34701.png)
The Code :
```c++
const int LEDPin = 13;
const int LDRPin      = A1; 
int sensorValue = 0;

void setup () {
  pinMode(LEDPin, OUTPUT);
  Serial.begin(9600);
}

void loop(){
  sensorValue = analogRead(LDRPin);
  Serial.print("sensor = " );
  Serial.println(sensorValue);

  if(sensorValue<160)
  {
     digitalWrite(LEDPin, HIGH);
  }
  else
  {
     digitalWrite(LEDPin, LOW);
  }

delay(500);
}
//End of LOOP

```
## Electronic circuit for button sensor (Digital) :
- Circuit design link in tinkercad :<br> https://www.tinkercad.com/things/amBkkopbnpL
- What is the Grove Button module ? <br>
Is a simple sensor. It only has two modes: ON and OFF, or more commonly referred to in the Arduino language, HIGH or LOW. Pushing a button activates its high state, while releasing it activates its low state.
![Sizzling Hillar](https://user-images.githubusercontent.com/108204114/182065835-70dcf34a-99a0-4c7a-a22b-c448a03776ae.png)
The Code :
```c++
int buttonPin = 2;
int ledPin = 13 ;
int buttonState =0;

void setup()
{
  pinMode(ledPin, OUTPUT);
  pinMode(buttonPin, INPUT);
}

void loop()
{
  
  buttonState = digitalRead(buttonPin);
  if(buttonState == HIGH){
      digitalWrite(ledPin, HIGH);
  }else{
      digitalWrite(ledPin, LOW);
  }
  
 
}
```

### Reference: <br>
https://sensorkit.arduino.cc/sensorkit/module/lessons/lesson/02-the-button
<br>
https://www.digikey.com/en/maker/projects/learn-to-use-the-arduinos-analog-io/d3215f289c714847a6576a73717cd161

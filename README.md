# Experiment-no-6-DC-Motor-Speed-Control-Using-Arduino
### AIM : To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
•	Arduino UNO board
•	L293D driver
•	12V DC motor
•	10K ohm potentiometer
•	Pushbutton
•	12V source
•	Breadboard
•	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).
Arduino DC motor control circuit:
Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 
 
The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)
TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

### PRGORAM 
```
#define m1 2

#define m2 3

int output;

int pin = 6;

void setup()

{

pinMode(m1, OUTPUT);

pinMode(m2, OUTPUT);

Serial.begin(9600);

}

void loop()

{

digitalWrite(m1, HIGH);

digitalWrite(m2, LOW);

delay(2000);

digitalWrite(m1, LOW);

delay(1000);

digitalWrite(m1, LOW);

digitalWrite(m2, HIGH);

delay(2000);

digitalWrite(m2, LOW);

delay(1000);

output = map(analogRead(A0), 0, 1023, 0, 255);

Serial.println(output);

analogWrite(pin, output);

if (output>=600)

{

digitalWrite(2,HIGH);
}

else

digitalWrite(2, LOW);
delay(1000);

}
```
### OUTPUT
### before simulation:
![243695210-9ea487db-1d3e-4d66-bd79-42ca52912ae1 1](https://github.com/sanjeevraj0987/Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino/assets/120698946/0b141b7b-f2ab-40a8-925b-ca5814884c89)
### after simulation:
![image](https://github.com/sanjeevraj0987/Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino/assets/120698946/d4122bab-0eae-4795-88b8-ba3856c31e5a)








### RESULTS 
To control the speed and the direction of a DC motor using L293D driven successfully


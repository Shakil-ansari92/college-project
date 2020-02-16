# college-project
 # Robotic arm using arduino

# code for running the robotic arm
\******** # start # *******\

//add servo library
#include <Servo.h>
 
//define our servos
Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;
 
//define our potentiometers
int pot1 = A1;
int pot2 = A2;
int pot3 = A3;
int pot4 = A4;
 
//variable to read the values from the analog pin (potentiometers)
int valPot1;
int valPot2;
int valPot3;
int valPot4;
int pin1;
int pin2;
int a,b;
int val1,val2,val3,val4;
void setup()
{
  //attaches our servos on pins PWM 3-5-6-9 to the servos
  servo1.attach(3);
  servo1.write(0);  //define servo1 start position
  servo2.attach(5);
  servo2.write(90); //define servo2 start position
  servo3.attach(6);
  servo3.write(90); //define servo3 start position
  servo4.attach(9);
  servo4.write(70); //define servo4 start position
Serial.begin(9600);
pinMode(pin1,INPUT);
pinMode(pin2,INPUT);
}
 
void loop()
{
  //reads the value of potentiometers (value between 0 and 1023)
  a=digitalRead(pin1);
  b=digitalRead(pin2);
  valPot1 = analogRead(pot1);
  valPot1 = map (valPot1, 0, 1023, 0, 180); //scale it to use it with the servo (value between 0 and 180)
  servo1.write(valPot1); //set the servo position according to the scaled value
 
  valPot2 = analogRead(pot2);
  valPot2 = map (valPot2, 0, 1023, 0, 180);
  servo2.write(valPot2);
 
  valPot3 = analogRead(pot3);
  valPot3 = map (valPot3, 0, 1023, 0, 180);
  servo3.write(valPot3);
 
  valPot4 = analogRead(pot4);
  valPot4 = map (valPot4, 0, 1023, 70, 150);
  servo4.write(valPot4);

  if(a==HIGH)
  {
    val1=valPot1;
    val2=valPot2;
    val3=valPot3;
    val4=valPot4;
  }
  if (b == HIGH)
  {
    for(int i=0;i<val1;i++)
    {
      servo1.write(i);
      delay(100);
    }
    for(int i=0;i<val2;i++)
    {
      servo2.write(i);
      delay(100);
    }
    for(int i=0;i<val3;i++)
    {
      servo3.write(i);
      delay(100);
    }
    for(int i=0;i<val4;i++)
    {
      servo4.write(i);
      delay(100);
    }
  }
}

  

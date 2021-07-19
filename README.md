# Bluetooth.robocar
#include <AFMotor.h>

AF_DCMotor motor1(1);
AF_DCMotor motor3(3);
  int led=9;
char bt='S';
void setup()
{
  Serial.begin(9600);
  pinMode(led,OUTPUT);
  motor1.setSpeed(255);
  motor3.setSpeed(255);

  Stop();
}


void loop() {
 
bt=Serial.read();

if(bt=='F')
{
 forward(); 
}

if(bt=='B')
{
 backward(); 
}

if(bt=='L')
{
 left(); 
}

if(bt=='R')
{
 right(); 
}

if(bt=='W')
{
 Stop(); 
}
if(bt=='A')
{
LED_ON();
}
if(bt=='O')
{
  LED_OFF();
}
}

void forward()
{
     motor1.run(FORWARD);
  motor3.run(FORWARD);
  digitalWrite(9,HIGH);
}

void backward()
{
     motor1.run(BACKWARD);
  motor3.run(BACKWARD);
digitalWrite(9,HIGH);
}
void left()
{
  motor1.run(FORWARD);
  motor3.run(BACKWARD);
 digitalWrite(9,HIGH);
}
void right()
{
  motor1.run(BACKWARD);
  motor3.run(FORWARD);
digitalWrite(9,HIGH);
}
void Stop()
{
  motor1.run(RELEASE);
  motor3.run(RELEASE);
digitalWrite(9,HIGH);
}
void LED_ON()
{
  digitalWrite(9,HIGH);
}
void LED_OFF()
{
  digitalWrite(9,LOW);
}
  

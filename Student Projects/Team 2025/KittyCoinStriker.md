---
title:  Kitty Coin Striker
layout: default
parent: Team 2025
grand_parent: Student Projects
---

##  Kitty Coin Striker

by Aleksandra & Carol

Project Image             |  In Action
:-------------------------:|:-------------------------:
<img src="media/kitty.heic" alt="drawing" width="365"/>  |   <video width="365" controls><source src="media/kitty.mov" type="video/mp4"></video>


The goal was to make electric piggy bank. We got inspired by the kitten pulling the coins into jar, but then building it we gamified it even more, added the gate for the coins to collect.

### Arduino Code


```c++
int myPhotoresistor = A0;
#include <Servo.h> // include Servo library
Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards
void setup() {
  pinMode(myPhotoresistor, INPUT);
  Serial.begin(9600);
  myservo.attach(8);  // attaches the servo on pin 9 to the servo object
}
void loop() {
   int lightvalue = analogRead(myPhotoresistor);
    if(lightvalue<490) {
  myservo.write(100); //Turn on LED if value us lower then 500
   delay(1000);
  myservo.write(20);
    delay(1000);
  }
Serial.println(lightvalue);
}

```
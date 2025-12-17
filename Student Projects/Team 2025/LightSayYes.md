---
title:  When Light Says Yes
layout: default
parent: Team 2025
grand_parent: Student Projects
---

## When Light Says Yes

by Zarifa Nabila & [Redacted]

Project Image             |  In Action
:-------------------------:|:-------------------------:
<img src="media/lightyes.heic" alt="drawing" width="365"/>  |   <video width="365" controls><source src="" type="video/mp4"></video>

This project utilises light to determine when an interaction is permitted. When the environment is bright enough, the system becomes active. A ball placed on a paper-built ramp then acts as the trigger: as it moves closer, an ultrasonic sensor detects it and activates a servo motor that shifts part of the ramp. In low light, the same action has no effect. The interaction combines light, gravity, and a simple physical object to control movement.

### Arduino Code


```c++
#include <Servo.h>
Servo lift;
const int trigPin = 9;
const int echoPin = 10;
const int liftPin= 11;
const int redPin = 2;
const int greenPin = 3;


float duration, distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  lift.attach(liftPin);
  lift.write(0);
  Serial.begin(9600);
}

void loop() {
  int value = analogRead(A0);

  Serial.print("Value: ");
  Serial.println(value);

  if (value > 500) {
    digitalWrite(redPin, LOW);
    digitalWrite(greenPin, HIGH);

    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);

    duration = pulseIn(echoPin, HIGH);
    distance = (duration*.0343)/2;
    Serial.print("Distance: ");
    Serial.println(distance);

    if (distance >= 4) {
      lift.write(180);
      delay(3000);
      lift.write(0);
    }
  } else {
    digitalWrite(redPin, HIGH);
    digitalWrite(greenPin, LOW);
  }
}

```

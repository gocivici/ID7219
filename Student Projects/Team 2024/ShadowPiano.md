---
title:  Shadow Piano
layout: default
parent: Team 2024
grand_parent: Student Projects
---

##  Shadow Piano

by Ezgi Okka, Jayneet Sanchaniya & Jorven Viilik

Project Image             |  In Action
:-------------------------:|:-------------------------:
<img src="media/piano.jpg" alt="drawing" width="365"/>  |   <video width="365" controls><source src="media/piano.mp4" type="video/mp4"></video>


Short summary: Shadow Piano uses the absence of light to play specific notes (C, E, G). A player can interact with the piano by hovering his/hers hands above 3 photoresistors. Not exactly Beethoven, but fun to us. 

### Arduino Code


```c++
int prpin = A0;
int prpin1 = A1;
int prpin2 = A2;
int buzzer = 7;
int threshold = 500;
int threshold1 = 100;
int threshold2 = 900;

void setup() {
  pinMode(buzzer, OUTPUT);
  pinMode(prpin, INPUT);
  pinMode(prpin1, INPUT);
  pinMode(prpin2, INPUT);
  Serial.begin(9600);
}
void loop() {
  int  sensor= analogRead(prpin);
  int  sensor1= analogRead(prpin1);
  int  sensor2= analogRead(prpin2);
  Serial.print("sensor = ");
  Serial.print(sensor);
  Serial.print(", sensor1 = ");
  Serial.print(sensor1);
  Serial.print(", sensor2 = ");
  Serial.println(sensor2);
  int selectpitch = 0;
  if (sensor < threshold) {
    selectpitch = 1;
  } else if (sensor1 < threshold1) {
    selectpitch = 2;
  } else if (sensor2 < threshold2) {
    selectpitch = 3;
  }
  switch (selectpitch) {
    case 1:
      tone(buzzer, 262);
      break;
    case 2:
      tone(buzzer, 330);
      break;
    case 3:
      tone(buzzer, 392);
      break;
    default:
      noTone(buzzer);
      break;
  }
  delay(100);
}

```
arduino_codigo

int trig = 7;
int echo = 8;
int duration = 0;
int distance = 0;

void setup() {
   Serial.begin(9600);
   pinMode(trig, OUTPUT);
   pinMode(echo, INPUT);
   digitalWrite(trig, LOW);
}

void loop() {
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  duration = pulseIn (echo, HIGH);
  distance = duration/58.2;
  Serial.println(distance);     
  delay (500);
}


raspberry_code

import serial
import time

ser = serial.Serial('/dev/ttyACM0', 9600)

while 1:

      recSer = ser.readline().decode('utf-8')
      recSer.rstrip()
      
      distance = int(recSer)
      
      print("Distance:" + str(distance) + "cm ")
      
      time.sleep(0.5)

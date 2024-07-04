# Car Speed Detector using Arduino and IR Sensors


## Introduction
This project utilizes Arduino and IR sensors to create a car speed detector, ideal for applications in traffic monitoring and safety. By integrating an Arduino Uno, infrared sensors, and an LCD display,
you can accurately measure and display vehicle speeds.

## Components Required
Arduino UNO
IR Sensors
16×2 LCD Display
Resistors (100R, 4.7k, 1k)
Breadboard
Jumper Wires
Battery Clip
9V Battery

## Working Principle
Sensor Setup: Two IR sensors are placed at a known distance apart.
Speed Detection: Arduino continuously monitors the IR sensors. When a vehicle passes the first sensor, it records the time.
Calculation: As the vehicle passes the second sensor, Arduino calculates the time difference and computes the speed based on the distance between sensors.
Display: The calculated speed is displayed on the 16×2 LCD display.

## Proteus Simulation
Components: Simulates with Arduino UNO, push buttons instead of IR sensors, 16×2 LCD, and a buzzer for feedback.
Simulation Flow: Displays "Searching" on LCD when a vehicle crosses the first virtual sensor. Upon reaching the second sensor, it calculates and displays the speed in km/h. 
Alerts for speeds exceeding 50 km/h with "Over Speeding" message and buzzer activation.

## Arduino code
#include<LiquidCrystal.h>
LiquidCrystal lcd(2, 3, 4, 5, 6, 7);

int timer1;
int timer2;

float Time;

int flag1 = 0;
int flag2 = 0;

float distance = 5.0;
float speed;

int ir_s1 = A0;
int ir_s2 = A1;

int buzzer = 13;

void setup(){
  pinMode(ir_s1, INPUT);
  pinMode(ir_s2, INPUT);
  pinMode(buzzer, OUTPUT);
  
  lcd.begin(16,2);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print(" WELCOME To  My ");
  lcd.setCursor(0,1);
  lcd.print("YouTube  Channel");
  delay(2000);
  lcd.clear();
}

void loop() {
if(digitalRead (ir_s1) == LOW && flag1==0){timer1 = millis(); flag1=1;}

if(digitalRead (ir_s2) == LOW && flag2==0){timer2 = millis(); flag2=1;}

if (flag1==1 && flag2==1){
     if(timer1 > timer2){Time = timer1 - timer2;}
else if(timer2 > timer1){Time = timer2 - timer1;}
 Time=Time/1000;//convert millisecond to second
 speed=(distance/Time);//v=d/t
 speed=speed*3600;//multiply by seconds per hr
 speed=speed/1000;//division by meters per Km
}

if(speed==0){ 
lcd.setCursor(0, 1); 
if(flag1==0 && flag2==0){lcd.print("No car  detected");}
                    else{lcd.print("Searching...    ");} 
}
else{
    lcd.clear(); 
    lcd.setCursor(0, 0); 
    lcd.print("Speed:");
    lcd.print(speed,1);
    lcd.print("Km/Hr  ");
    lcd.setCursor(0, 1); 
  if(speed > 50){lcd.print("  Over Speeding  "); digitalWrite(buzzer, HIGH);}
            else{lcd.print("  Normal Speed   "); }    
    delay(3000);
    digitalWrite(buzzer, LOW);
    speed = 0;
    flag1 = 0;
    flag2 = 0;    
 }
}

## Conclusion
This project provides a practical tool for speed detection using readily available components and Arduino technology. It offers educational value and practical applications in traffic management and safety.

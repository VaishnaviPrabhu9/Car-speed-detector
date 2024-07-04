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

## Conclusion
This project provides a practical tool for speed detection using readily available components and Arduino technology. It offers educational value and practical applications in traffic management and safety.

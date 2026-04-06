# Experiment 3: Ultrasonic Sensor Interfacing with STM32

## Aim
To interface an HC-SR04 ultrasonic sensor with STM32 and measure distance using the time-of-flight principle.

---

## Components Required
- STM32 Nucleo-F446RE  
- HC-SR04 Ultrasonic Sensor  
- Jumper Wires  
- USB Cable  
- STM32CubeIDE  
- STM32CubeMX  

---

## Description
This experiment demonstrates how a microcontroller can measure distance using an ultrasonic sensor. The HC-SR04 sensor is interfaced with STM32, and the distance is calculated based on the time taken by ultrasonic waves to travel and return.

The measured distance is used to control an LED based on predefined conditions.

---

## Theory
The HC-SR04 ultrasonic sensor works on the principle of time-of-flight. It emits ultrasonic waves and measures the time taken for the waves to reflect back from an object.

A trigger pulse is sent to the sensor, which generates ultrasonic waves. The Echo pin produces a pulse whose duration represents the travel time of the wave.

The distance is calculated using the formula:

Distance = (Velocity × Time) / 2  

Where the velocity of sound is approximately 343 m/s.

STM32 timers are used to measure this time accurately, enabling precise distance calculation.

---

## Procedure
1. Open STM32CubeMX  
2. Select STM32F446RE  
3. Configure TRIG pin as output  
4. Configure ECHO pin as input  
5. Configure LED pin as output  
6. Enable timer for time measurement  
7. Generate code  
8. Open project in STM32CubeIDE  
9. Write sensor interfacing logic  
10. Build and run  

---

## Code
timep = TIM2->CCR2;
dist = (timep * 0.0343f) / 2.0f;

---

## Result
The ultrasonic sensor successfully measured distance, and the LED responded based on the measured distance values.

---

## Learning Outcome
- Learned ultrasonic sensor interfacing  
- Understood time-of-flight principle  
- Gained experience with timer usage  
- Improved embedded programming skills  

---

## Conclusion
This experiment demonstrates how distance measurement can be implemented using ultrasonic sensors and microcontrollers. It is widely used in robotics, automation, and obstacle detection systems.

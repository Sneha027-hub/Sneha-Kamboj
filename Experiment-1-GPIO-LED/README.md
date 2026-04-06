# Experiment 1: GPIO LED Control using STM32

## Aim
To configure a GPIO pin as output and control an onboard LED using STM32 microcontroller.

---

## Components Required
- STM32 Nucleo-F446RE  
- USB Cable  
- STM32CubeIDE  
- STM32CubeMX  

---

## Description
This experiment demonstrates the basic concept of GPIO (General Purpose Input/Output) in embedded systems. A GPIO pin is configured as a digital output to control an onboard LED.

By setting the GPIO pin to HIGH or LOW, the LED can be turned ON or OFF. This experiment forms the foundation for understanding how microcontrollers interact with external hardware components.

---

## Theory
GPIO pins in STM32 microcontrollers are flexible pins that can be configured as either input or output.  

In this experiment, pin PA5 is configured as an output pin and is connected to the onboard LED. When the pin is set to HIGH, the LED turns ON, and when set to LOW, the LED turns OFF.

The configuration of GPIO pins is performed using STM32CubeMX, while control is implemented in STM32CubeIDE using HAL functions.

---

## Procedure
1. Open STM32CubeMX  
2. Select STM32F446RE  
3. Configure PA5 as GPIO output  
4. Generate code  
5. Open project in STM32CubeIDE  
6. Write LED control logic  
7. Build and run  

---

## Code
HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);

---

## Result
The onboard LED was successfully controlled using the GPIO output pin. The LED turned ON and OFF based on the pin state.

---

## Learning Outcome
- Learned GPIO configuration  
- Understood digital output control  
- Gained experience with STM32 tools  

---

## Conclusion
This experiment provides a basic understanding of GPIO functionality and demonstrates how microcontrollers control external devices. It serves as a foundation for more advanced embedded system applications.

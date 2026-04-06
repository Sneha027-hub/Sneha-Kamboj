# Experiment 2: Push Button Controlled LED using STM32

## Aim
To interface a push button as a digital input and control an LED by toggling its state on each button press.

---

## Components Required
- STM32 Nucleo-F446RE  
- USB Cable  
- STM32CubeIDE  
- STM32CubeMX  

---

## Description
This experiment demonstrates how a microcontroller can read input from a push button and control an output device such as an LED.

A push button is used as a digital input, and based on its state, the LED is toggled. This experiment introduces the concept of input-output interfacing in embedded systems.

---

## Theory
GPIO pins in STM32 can be configured as either input or output.  

In this experiment, pin PC13 is configured as a digital input and is connected to the onboard push button. When the button is pressed, the input signal changes, which is detected by the microcontroller.

Pin PA5 is configured as a digital output and is connected to the onboard LED. When the button is pressed, the microcontroller toggles the LED state.

A small delay is used to avoid multiple toggles caused by mechanical bouncing of the button (debouncing).

---

## Procedure
1. Open STM32CubeMX  
2. Select STM32F446RE  
3. Configure PA5 as output (LED)  
4. Configure PC13 as input (Push Button)  
5. Generate code  
6. Open project in STM32CubeIDE  
7. Write toggle logic  
8. Build and run  

---

## Code
while (1)
{
  if (HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13) == 0)
  {
    HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
    HAL_Delay(200);
  }
}

---

## Result
The LED successfully toggled its state on each button press and maintained its state after release.

---

## Learning Outcome
- Learned digital input and output interfacing  
- Understood push button operation  
- Learned debouncing concept  
- Gained experience with STM32 programming  

---

## Conclusion
This experiment demonstrates how input signals can be used to control output devices in embedded systems. It forms a basic foundation for event-driven system design.

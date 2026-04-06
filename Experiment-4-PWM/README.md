# Experiment 4: PWM Signal Generation using STM32

## Aim
To generate a PWM signal using a timer on STM32 and control LED brightness by varying the duty cycle.

---

## Components Required
- STM32 Nucleo-F446RE  
- USB Cable  
- STM32CubeIDE  
- STM32CubeMX  

---

## Description
This experiment demonstrates how a microcontroller can generate a Pulse Width Modulation (PWM) signal to control the brightness of an LED.

By varying the duty cycle of the PWM signal, the average voltage across the LED changes, which results in different brightness levels. This technique is widely used in embedded systems for controlling analog devices using digital signals.

---

## Theory
Pulse Width Modulation (PWM) is a technique in which a digital signal is switched ON and OFF at a fixed frequency while varying the duty cycle.

The duty cycle is defined as the percentage of time the signal remains HIGH during one complete cycle. A higher duty cycle results in a higher average voltage and increased brightness.

STM32 microcontrollers use timers to generate PWM signals. The timer uses:
- Prescaler (PSC) to divide clock frequency  
- Auto Reload Register (ARR) to define period  
- Capture Compare Register (CCR) to define duty cycle  

In PWM mode:
- Output is HIGH when counter < CCR  
- Output is LOW when counter ≥ CCR  

---

## Procedure
1. Open STM32CubeMX  
2. Select STM32F446RE  
3. Configure PA5 as TIM2 channel  
4. Set timer parameters (PSC and ARR)  
5. Generate code  
6. Open project in STM32CubeIDE  
7. Write PWM control logic  
8. Build and run  

---

## Code
HAL_TIM_PWM_Start(&htim2, TIM_CHANNEL_1);

while (1)
{
  for(int x = 0; x < 1000; x++)
  {
    __HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_1, x);
    HAL_Delay(1);
  }

  for(int x = 1000; x > 0; x--)
  {
    __HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_1, x);
    HAL_Delay(1);
  }
}

---

## Observation

| CCR Value | Duty Cycle (%) | Brightness Level |
|----------|----------------|------------------|
| 0        | 0              | OFF              |
| 250      | 25             | Low              |
| 500      | 50             | Medium           |
| 750      | 75             | High             |
| 1000     | 100            | Maximum          |

---

## Result
PWM signal was successfully generated and LED brightness was controlled by varying the duty cycle from 0% to 100%.

---

## Learning Outcome
- Learned PWM signal generation  
- Understood duty cycle concept  
- Gained experience with timer configuration  
- Improved embedded programming skills  

---

## Conclusion
This experiment demonstrates how PWM can be used to control analog outputs using digital techniques. It is widely used in applications such as motor control, LED dimming, and power regulation.

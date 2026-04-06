# Experiment 6: FreeRTOS Task Implementation using STM32

## Aim
To develop a basic FreeRTOS-based project on STM32 and validate LED blinking using a single RTOS task.

---

## Components Required
- STM32 Nucleo-F446RE  
- USB Cable  
- STM32CubeIDE  
- STM32CubeMX  

---

## Description
This experiment demonstrates the use of a Real-Time Operating System (FreeRTOS) in an embedded system. A task is created to control LED blinking, and the scheduler manages its execution.

The experiment shows how multitasking can be achieved efficiently using RTOS instead of a traditional super loop approach.

---

## Theory
A Real-Time Operating System (RTOS) manages multiple tasks using a scheduler. Each task has its own stack, priority, and execution state.

In this experiment, FreeRTOS is configured using CMSIS-RTOS v2. A task is created using the RTOS API, and it toggles the onboard LED periodically.

The function osDelay() is used to introduce delay in the task. Unlike traditional delay functions, it pauses only the current task, allowing the scheduler to execute other tasks.

This results in efficient CPU utilization and accurate timing.

---

## Procedure
1. Open STM32CubeMX  
2. Select STM32F446RE  
3. Configure PA5 as GPIO output  
4. Enable FreeRTOS (CMSIS_V2)  
5. Create a task (Task_1)  
6. Configure system clock  
7. Generate code  
8. Open project in STM32CubeIDE  
9. Configure SWV debugging  
10. Build and run  

---

## Code
void Task1_function(void *argument)
{
  for(;;)
  {
    HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
    printf("Task_1 Executing for LED Toggle\n");
    osDelay(500);
  }
}

---

## Observation
- LED toggled at regular intervals  
- SWV ITM console displayed task messages  
- Task execution was consistent and stable  

---

## Result
A FreeRTOS task was successfully created and executed. LED blinking and SWV output confirmed correct task scheduling and execution.

---

## Learning Outcome
- Learned RTOS fundamentals  
- Understood task creation and scheduling  
- Gained experience with FreeRTOS APIs  
- Learned SWV debugging techniques  

---

## Conclusion
This experiment demonstrates the advantages of RTOS in embedded systems. It provides efficient multitasking, better CPU utilization, and scalability for complex real-time applications.

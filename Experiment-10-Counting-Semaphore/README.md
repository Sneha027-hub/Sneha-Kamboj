# RTOS Experiment 10 – Counting Semaphore using FreeRTOS

## Aim
To model a limited shared resource using a FreeRTOS counting semaphore and study access control when multiple tasks request the resource simultaneously.

---

# Apparatus Required
- STM32 Nucleo-F446RE Development Board
- USB Type-A to Mini-B Cable
- Ultrasonic Sensor
- STM32CubeIDE
- STM32CubeMX

---

# Introduction

In Real-Time Operating Systems (RTOS), multiple tasks may attempt to access a shared hardware or software resource simultaneously. Without proper synchronization, this can lead to resource conflicts, data corruption, and unpredictable system behavior.

To avoid such problems, synchronization mechanisms like semaphores are used. A semaphore controls access to shared resources among multiple tasks.

A Counting Semaphore allows more than one task to access a resource at the same time depending on the semaphore count value. It is useful when multiple identical resources are available in the system.

---

# Theory

## Counting Semaphore

A Counting Semaphore is a synchronization primitive used in RTOS to manage access to shared resources.

It maintains:
- Maximum count
- Current available count

### Working Principle

### Acquire Operation
When a task requests a resource:
- If semaphore count > 0:
  - Access is granted
  - Count decreases
- If semaphore count = 0:
  - Task enters blocked state
  - Waits until resource becomes available

### Release Operation
When the task finishes:
- Semaphore is released
- Count increases
- Waiting tasks may resume execution

---

# Resource Sharing and Interleaving

In this experiment, three tasks:
- Task A
- Task B
- Task C

share a common ITM trace output resource.

Since the counting semaphore allows multiple tasks to access the resource simultaneously, outputs from different tasks become interleaved due to:
- Context switching
- Preemptive scheduling
- Shared communication channel

This demonstrates that counting semaphores control resource quantity but do not provide strict mutual exclusion.

---

# Objectives
- To understand counting semaphores in FreeRTOS
- To study task synchronization
- To observe resource sharing
- To analyze task interleaving
- To understand preemptive scheduling and context switching

---

# Software and Hardware Requirements

## Hardware
- STM32 Nucleo-F446RE Board
- USB Cable
- Ultrasonic Sensor

## Software
- STM32CubeMX
- STM32CubeIDE
- FreeRTOS

---

# Procedure

## Step 1
Open STM32CubeMX.

## Step 2
Select the STM32L446RE microcontroller.

## Step 3
Configure clock settings to 84 MHz.

## Step 4
Configure SYS settings:
- Debug: Trace Asynchronous SW
- Timebase Source: TIM6

## Step 5
Enable FreeRTOS middleware using CMSIS_V2 interface.

## Step 6
Create three tasks:
- TaskA
- TaskB
- TaskC

## Step 7
Add a Counting Semaphore from:
- Timers and Semaphores section

## Step 8
Enable:
USE_NEWLIB_REENTRANT

## Step 9
Generate project code.

## Step 10
Open project in STM32CubeIDE.

## Step 11
Configure SWV ITM Trace debugging.

## Step 12
Open main.c and add semaphore code.

## Step 13
Build the project and remove all compilation errors.

## Step 14
Start debugging and observe output in SWV ITM Data Console.

---

# Program Code

## Header File

```c
#include<stdio.h>
```

## SWV ITM Console Function

```c
int _write(int file, char *ptr, int len)
{
    for(int i = 0; i < len; i++)
    {
        ITM_SendChar(*ptr++);
    }

    return len;
}
```

## Task A

```c
void func_TaskA(void *argument)
{
    char ch = 'A';

    for(;;)
    {
        osSemaphoreAcquire(myCountingSem01Handle, osWaitForever);

        printf("1");

        for(int i = 0; i < 10; i++)
        {
            printf("%c", ch);
            HAL_Delay(50);
        }

        osSemaphoreRelease(myCountingSem01Handle);

        osDelay(5);
    }
}
```

## Task B

```c
void func_TaskB(void *argument)
{
    char ch = 'B';

    for(;;)
    {
        osSemaphoreAcquire(myCountingSem01Handle, osWaitForever);

        printf("2");

        for(int i = 0; i < 10; i++)
        {
            printf("%c", ch);
            HAL_Delay(50);
        }

        osSemaphoreRelease(myCountingSem01Handle);

        osDelay(5);
    }
}
```

## Task C

```c
void func_TaskC(void *argument)
{
    char ch = 'C';

    for(;;)
    {
        osSemaphoreAcquire(myCountingSem01Handle, osWaitForever);

        printf("3");

        for(int i = 0; i < 10; i++)
        {
            printf("%c", ch);
            HAL_Delay(50);
        }

        osSemaphoreRelease(myCountingSem01Handle);

        osDelay(5);
    }
}
```

---

# Flow of Execution

1. Task requests semaphore
2. Semaphore checks count
3. Access granted if resource available
4. Task prints output
5. Task releases semaphore
6. Next waiting task gets access

---

# Observation

During execution of the program on the SWV ITM Data Console, outputs from Task A, Task B, and Task C were displayed continuously. Since all tasks were accessing the same ITM trace output resource using a counting semaphore, task outputs became interleaved.

Mixed character patterns such as:
- ACACACAC
- BABABABA
- CBCBCBCB

were observed. This showed that multiple tasks were running concurrently and the RTOS scheduler was switching between tasks rapidly.

The experiment also showed that:
- Multiple tasks can access the shared resource depending on semaphore count.
- Context switching occurs frequently in preemptive scheduling.
- Counting semaphores control access quantity but not exclusive ownership of the resource.

---

# Observation Table

| Observation No. | Query | Response |
|---|---|---|
| 1 | How many tasks are able to use the ITM trace resource concurrently? | Multiple tasks may request access simultaneously, but actual communication occurs sequentially on the shared ITM trace resource. |
| 2 | Comment on interleaving of tasks. | Outputs from different tasks appeared mixed due to context switching and concurrent execution. |
| 3 | Which scheduling technique causes interleaving? | Preemptive scheduling and time slicing caused interleaving of task outputs. |
| 4 | What happened after changing delays or priorities? | Changing delays reduced switching frequency, while higher priority tasks appeared more frequently in the output. |

---

# Sample Output

```text
1AAAAAAAAAA
2BBBBBBBBBB
3CCCCCCCCCC

ACACACAC
BABABABA
CBCBCBCB
```

---

# Analysis

The experiment demonstrated practical implementation of counting semaphores in FreeRTOS for shared resource management.

Three different tasks attempted to access the same ITM trace output simultaneously. Since the semaphore count allowed more than one task to access the resource, task outputs became interleaved.

This experiment clearly demonstrated:
- Resource sharing
- Concurrent execution
- Task synchronization
- Context switching
- Preemptive scheduling

The output patterns confirmed that counting semaphores improve resource utilization but do not guarantee atomic access to communication peripherals.

---

# Result

The experiment was performed successfully and the working of a FreeRTOS counting semaphore was verified. Multiple tasks shared the ITM trace resource simultaneously, and interleaved outputs were observed due to preemptive scheduling and context switching.

---

# Conclusion

The experiment successfully demonstrated the implementation of a counting semaphore in FreeRTOS using STM32. It was observed that counting semaphores allow multiple tasks to access a shared resource based on the semaphore count value, thereby improving resource utilization and system throughput.

However, because multiple tasks were allowed to access the same communication interface simultaneously, outputs became interleaved. This proved that counting semaphores manage the number of accessible resources but do not provide strict mutual exclusion.

The experiment also helped in understanding:
- RTOS task scheduling
- Context switching
- Task synchronization
- Shared resource management

Overall, the experiment provided practical knowledge of synchronization mechanisms in embedded real-time systems and highlighted the importance of choosing appropriate synchronization techniques depending on system requirements.

---

# Reflection Summary

This experiment provided practical understanding of resource sharing and synchronization in Real-Time Operating Systems. By implementing multiple tasks using FreeRTOS and controlling access through a counting semaphore, the behavior of concurrent task execution was clearly observed.

The interleaving of outputs on the SWV ITM Data Console demonstrated the effects of context switching and preemptive scheduling in RTOS environments. It also highlighted that counting semaphores are useful for managing multiple instances of shared resources but are not suitable for ensuring exclusive access to communication peripherals.

Through this experiment, important RTOS concepts such as:
- Task scheduling
- Synchronization
- Semaphore handling
- Context switching
- Resource management

were understood practically. The experiment emphasized the importance of selecting the correct synchronization mechanism for maintaining both system efficiency and data integrity.

---

# Learning Outcomes

After performing this experiment, the following concepts were understood:
- FreeRTOS task management
- Counting semaphore implementation
- Shared resource synchronization
- Context switching in RTOS
- Preemptive scheduling behavior
- Task interleaving
- Resource allocation and access control

---

# Applications
- Embedded Systems
- Robotics
- Industrial Automation
- IoT Devices
- Real-Time Monitoring Systems
- Multi-threaded Embedded Applications

---

# Advantages of Counting Semaphore
- Efficient resource utilization
- Allows concurrent task execution
- Improves system throughput
- Useful for managing resource pools

---

# Limitations
- Does not guarantee mutual exclusion
- Shared outputs may become interleaved
- Can cause race conditions if used improperly

---

# Future Scope
- Implement mutex-based synchronization
- Compare binary semaphore and counting semaphore
- Study priority inversion handling
- Implement advanced RTOS synchronization techniques

---

# References
1. FreeRTOS Official Documentation
2. STM32CubeIDE Documentation
3. STM32CubeMX User Manual
4. ARM Cortex-M Programming Guide

---

# Author

## Vaasu Verma

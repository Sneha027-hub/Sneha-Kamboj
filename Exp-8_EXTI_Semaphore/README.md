# Experiment 8: Interrupt-Based Task Synchronization using Semaphore

## Aim
To design an event-driven system using external interrupts and binary semaphores for task synchronization.

---

## Introduction
Real-time systems often need to respond instantly to external events such as button presses or sensor triggers. Interrupts provide a mechanism for immediate response, while RTOS synchronization tools ensure efficient processing.

This experiment demonstrates how interrupts and semaphores work together to control task execution.

---

## Theory
Interrupt Service Routines (ISR) are used to handle hardware events. However, performing complex operations inside ISR can degrade system performance.

To overcome this:
- ISR performs minimal work  
- A binary semaphore is used to signal a task  
- The task performs the required processing  

This approach is known as deferred interrupt processing.

---

## Implementation
- External interrupt configured on push button  
- Binary semaphore created and initialized  
- Task designed to wait for semaphore signal  
- ISR releases semaphore upon button press  

---

## Observations
- Task remains in blocked state until interrupt occurs  
- On button press, semaphore is released and task executes  
- LED toggles only in response to the event  

---

## Result
The system successfully synchronized task execution with an external interrupt using a binary semaphore.

---

## Conclusion
Using semaphores with interrupts improves system responsiveness and ensures efficient CPU utilization by avoiding unnecessary task execution.

---

## Learning Outcomes
- Understanding of external interrupts (EXTI)  
- Knowledge of semaphore-based synchronization  
- Implementation of ISR-task communication  
- Experience with event-driven system design  

---

## Future Scope
- Use of counting semaphores and mutex  
- Handling multiple interrupt sources  
- Integration with real-time industrial applications  

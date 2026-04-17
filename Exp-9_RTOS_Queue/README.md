# Experiment 9: Inter-Task Communication using FreeRTOS Queue

## Aim
To implement data exchange between tasks using a queue in a FreeRTOS-based system.

---

## Introduction
In embedded systems, multiple tasks often need to exchange data efficiently. Direct sharing of variables can lead to data corruption and synchronization issues.

FreeRTOS provides queues as a reliable mechanism for inter-task communication.

---

## Theory
A queue in FreeRTOS is a thread-safe data structure that follows FIFO (First In First Out) order.

Key features:
- Safe data transfer between tasks  
- Built-in synchronization mechanism  
- Blocking capability for efficient CPU usage  

Queues enable the implementation of the producer-consumer model, where:
- Producer generates data  
- Consumer processes data  

---

## Implementation
- Two tasks were created: Producer and Consumer  
- A queue was initialized to store data  
- Producer task periodically sent data to the queue  
- Consumer task received and processed the data  

---

## Observations
- Producer generated data at regular intervals  
- Consumer retrieved data in correct sequence  
- Blocking ensured efficient synchronization between tasks  

---

## Result
The experiment successfully demonstrated reliable inter-task communication using a FreeRTOS queue.

---

## Conclusion
Queues provide an efficient and safe method for communication between tasks, making them essential for complex real-time systems.

---

## Learning Outcomes
- Understanding of queue-based communication  
- Implementation of producer-consumer model  
- Safe data handling in multitasking environment  
- Practical exposure to RTOS communication mechanisms  

---

## Future Scope
- Implementation of multiple queues  
- Optimization for high-speed data transfer  
- Integration with sensor-based applications  

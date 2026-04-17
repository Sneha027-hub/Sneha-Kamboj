# Experiment 7: Task Priority Scheduling in FreeRTOS

## Aim
To study the impact of task priority on execution behavior by implementing multiple tasks in a FreeRTOS environment.

---

## Introduction
In real-time embedded systems, efficient CPU utilization is achieved through proper scheduling of tasks. FreeRTOS uses a priority-based preemptive scheduler to manage multiple tasks running on a microcontroller.

This experiment focuses on understanding how task priorities influence execution order and system performance.

---

## Theory
FreeRTOS schedules tasks based on priority levels:
- A higher priority task preempts a lower priority task
- Tasks with equal priority share CPU time using time slicing
- Improper priority assignment may lead to starvation of lower priority tasks

This mechanism ensures that time-critical operations are executed promptly.

---

## Implementation
- Two independent tasks were created using FreeRTOS  
- Each task was assigned a specific priority  
- Both tasks performed LED toggling with equal delay  
- Execution behavior was monitored using SWV output  

---

## Observations
- Tasks with equal priority showed balanced execution  
- Increasing priority of one task caused it to dominate CPU usage  
- Lower priority task experienced reduced execution frequency  

---

## Result
The experiment successfully demonstrated the effect of priority-based scheduling on task execution and system behavior.

---

## Conclusion
Task priority plays a crucial role in real-time systems. Proper assignment ensures efficient CPU utilization and prevents performance issues such as starvation.

---

## Learning Outcomes
- Understanding of FreeRTOS task scheduling  
- Knowledge of priority-based execution  
- Practical experience with multitasking  
- Analysis of real-time system behavior  

---

## Future Scope
- Implementation of multiple tasks with dynamic priorities  
- Study of advanced scheduling techniques  
- Integration with synchronization mechanisms  

# Scheduling-Algorithms-of-CPU-in-OS-using-C-
Implemented several popular CPU scheduling algorithms like FCFS, RR etc

## Table of Contents
- [CPU-Scheduling-Algorithms](#cpu-scheduling-algorithms)
  - [Algorithms](#algorithms)
    - [First Come First Serve (FCFS)](#first-come-first-serve-fcfs)
    - [Round Robin with varying time quantum (RR)](#round-robin-with-varying-time-quantum-rr)
    - [Shortest Process Next (SPN)](#shortest-process-next-spn)
    - [Shortest Remaining Time (SRT)](#shortest-remaining-time-srt)
    - [Highest Response Ratio Next (HRRN)](#highest-response-ratio-next-hrrn)
    - [Feedback (FB)](#feedback-fb)
    - [Feedback with varying time quantum (FBV)](#feedback-with-varying-time-quantum-fbv)
    - [Aging](#aging)
  - [Installation](#installation)
  - [Input Format](#input-format)
  - [Contributors](#contributors)

## Algorithms

### CPU Scheduling Algorithms
First Come First Serve (FCFS)
First Come First Serve (FCFS) is a straightforward scheduling algorithm where the process that arrives first is executed first. It's simple but can lead to inefficiency if long-running processes arrive early, blocking shorter processes.

Round Robin with varying time quantum (RR)
Round Robin (RR) with a variable time quantum divides CPU time among processes. This approach adjusts the quantum dynamically, allocating more time to shorter processes to optimize performance.

Shortest Process Next (SPN)
Shortest Process Next (SPN) prioritizes processes based on their burst time, executing the shortest one first. It's non-preemptive, ensuring minimal waiting time for shorter tasks.

Shortest Remaining Time (SRT)
Shortest Remaining Time Next (SRT) is preemptive and similar to SPN but prioritizes processes based on their remaining time. It adapts well to dynamic burst times, minimizing waiting times effectively.

Highest Response Ratio Next (HRRN)
Highest Response Ratio Next (HRRN) prioritizes processes based on their response ratio (waiting time / burst time). It's non-preemptive and ideal for minimizing average waiting times when burst times vary.

Feedback (FB)
Feedback is a multi-level priority scheduling algorithm that uses multiple queues with varying priorities. It ensures higher priority processes are executed first while adjusting priorities dynamically.

Feedback with varying time quantum (FBV)
Feedback with varying time quantum uses multiple priority queues with different time quanta for each priority level. This approach optimizes CPU allocation by adjusting quantum sizes based on process priority.

Aging

- Xinu is an operating system developed at Purdue University. The scheduling invariant in Xinu assumes that at any
time, the highest priority process eligible for CPU service is executing, with round-robin scheduling for processes of
equal priority. Under this scheduling policy, the processes with the highest priority will always be executing. As a
result, all the processes with lower priority will never get CPU time. As a result, starvation is produced in Xinu when
we have two or more processes eligible for execution that have different priorities. For ease of discussion, we call the
set of processes in the ready list and the current process as the eligible processes.

- To overcome starvation, an aging scheduler may be used. On each rescheduling operation, a timeout for instance, the
scheduler increases the priority of all the ready processes by a constant number. This avoids starvation as each ready
process can be passed over by the scheduler only a finite number of times before it has the highest priority.

- Each process has an initial priority that is assigned to it at process creation. Every time the scheduler is called it takes
the following steps.
    - The priority of the current process is set to the initial priority assigned to it.
    - The priorities of all the ready processes (not the current process) are incremented by 1.
    - The scheduler choses the highest priority process from among all the eligible processes.

- Note that during each call to the scheduler, the complete ready list has to be traversed.
## Installation
1- Clone the repository

2- Install g++ compiler and make
```bash
sudo apt-get install g++ make
```
3- Compile the code using `make` command

4- Run the executable file

## Input Format
- Line 1: "trace" or "stats"
- Line 2: a comma-separated list telling which CPU scheduling policies to be analyzed/visualized along with
their parameters, if applicable. Each algorithm is represented by a number as listed in the
introduction section and as shown in the attached testcases.
Round Robin and Aging have a parameter specifying the quantum q to be used. Therefore, a policy
entered as 2-4 means Round Robin with q=4. Also, policy 8-1 means Aging with q=1.
 1. FCFS (First Come First Serve)
 2. RR (Round Robin)
 3. SPN (Shortest Process Next)
 4. SRT (Shortest Remaining Time)
 5. HRRN (Highest Response Ratio Next)
 6. FB-1, (Feedback where all queues have q=1)
 7. FB-2i, (Feedback where q= 2i)
 8. Aging
- Line 3: An integer specifying the last instant to be used in your simulation and to be shown on the timeline.
- Line 4: An integer specifying the number of processes to be simulated.
- Line 5: Start of description of processes. Each process is to be described on a separate line. For algorithms 1 through 7, each process is described using a comma-separated list specifying:

    1- String specifying a process name\
    2- Arrival Time\
    3- Service Time

- **Note:** For Aging algorithm (algorithm 8), each process is described using a comma-separated list specifying:

    1- String specifying a process name\
    2- Arrival Time\
    3- Priority
- Processes are assumed to be sorted based on the arrival time. If two processes have the same arrival time, then the one with the lower priority is assumed to arrive first.
> Check the attached [testcases](https://github.com/yousefkotp/CPU-Scheduling-Algorithms/tree/main/testcases) for more details.




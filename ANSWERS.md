# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:  A process is a complete program that operates independently and has its own memory that is unavailable to other programs. A thread is a smaller unit that operates within a process and shares memory with other threads. Because threads share data structures like processQueue and processMap without needing special communication, we used them in this assignment instead of using distinct processes, which would make data flow between them much more difficult. Since we create a new thread for each quantum a process runs, threads are also quicker and less expensive to create than entire processes.**

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer: A process is removed from the CPU and put at the end of the ready queue, where it waits for all other processes to have their turn before starting again, if it does not complete within its time quantum. This ensures equality since no process may delay others by taking too long.

 Example from my output: 
 
▶ P1 executing quantum [4000ms]
  ⏸ P1 completed quantum 4000ms │ Overall progress: [███████████████░░░░░] 76%
     Remaining time: 1239ms
  ↻ P1 yields CPU for context switch

  ➕ P1 (Priority: 3) added to ready queue │ Burst time: 5239ms
┌─ Ready Queue ─────────────────────────────────────────────────────────────────
│ [P3 → P4 → P5 → P6 → P7 → P8 → P9 → P10 → P11 → P12 → P13 → P1]
└───────────────────────────────────────────────────────────────────────────────

**

[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]



```

[Paste a relevant snippet from your program output here showing a process being re-queued]
```

**Explanation of example:      P1 was only permitted to run for 4000 ms out of a total of 5239 ms, leaving 1239 ms unfinished. The method was verified by the program.P1 was placed back at the very end of the queue, behind 11 other processes, when isFinished() returned false. Round-Robin is equal to everybody because P1 had to wait for everyone to take their turn before it could run again.    **
[Explain what's happening in the output snippet you pasted]

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:  P1 (burst time: 5239 ms, quantum: 4000 ms) passes through each state as follows:

New: When addProcessToQueue() calls a new Thread (process). Although the topic has been created, it has not yet been begun.
Runnable: When the scheduler loop calls currentThread.start(). P1 is prepared and just needs the CPU.
Running: When run() begins to run once the CPU has been assigned.

P1 running quantum [4000ms] is the output.


Waiting: When the main program calls currentThread and when Thread.sleep(stepTime) inside run() simulates execution.join() is awaiting P1's quantum completion.
Terminated: When the quantum expires and run() returns. When P1 re-enters the queue, a brand-new thread is formed because a completed thread cannot run again.

Output: P1's execution is complete!  **

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]


## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1:  Web server
An explanation:
When multiple users access a website at the same time, a web server employs Round-Robin to distribute the CPU equitably among all of them by creating a distinct thread for each request.
Why Round-Robin is effective in this situation:
It ensures that nobody is delayed by a single slow request. Because each thread receives equal CPU turns, a slow database request does not prevent a rapid page load, such as in our scenario when P6 (2231 ms) completed swiftly without waiting for the long P3 (9900 ms).

**Description**: 
[Describe the real-world scenario or application]

**Why Round-Robin works well here**: 
[Explain why Round-Robin scheduling is suitable. Consider fairness, responsiveness, predictability, etc.]

### Example 2:  Desktop  operating system
An explanation:
Round-Robin is used by a computer running a browser, music player, and file download at the same time to offer each program a small CPU time slice in turn.
Why Round-Robin is effective in this situation:
It ensures the responsiveness of all applications. Because every program only uses the CPU for a brief period of time before releasing it, no background process can cause the screen to freeze. This is exactly what our context switch counter (Feature 2) monitored: each time a program gives up control of the CPU to another.

**Description**: 
[Describe the real-world scenario or application]

**Why Round-Robin works well here**: 
[Explain why Round-Robin scheduling is suitable. Consider fairness, responsiveness, predictability, etc.]

---

## Summary

**Key concepts I understood through these questions:**
1. For simulations like this one, threads are easy to utilize and quick because they share memory within a process.
2. To ensure that every process has an equal and fair turn, Round-Robin places incomplete processes at the back of the queue.
3. A line of code is intimately linked to each thread state: new Thread() creates it, start() prepares it, run() runs it, sleep()/join() stops it, and returning from run() terminates it.

**Concepts I need to study more:**
1. How to use technologies like synchronized to protect shared data when many threads are running together.
2. How to extend this simulation to use the priority values from Feature 1 to actually decide which process runs next.

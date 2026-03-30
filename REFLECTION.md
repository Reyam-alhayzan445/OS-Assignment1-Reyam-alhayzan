# Reflection Questions

## Instructions
Answer the following questions about your learning experience. Each answer should be **at least 5-7 sentences** and show your understanding.

---

## Question 1: What did you learn about multithreading?

**Your Answer:  I didn't really get how threads operate in practice before this assignment. I discovered that although calling run() straight simply executes the code normally without any parallelism, invoking Thread.start() generates a new thread that runs concurrently with the main application. Additionally, I discovered that the main program waits for a thread to finish before continuing thanks to Thread.join(). A thread can pause for a predetermined amount of time without wasting CPU power by using Thread.sleep(). The most unexpected thing I learned is that we have to start a new thread each time a process re-enters the queue since once a thread is finished, it cannot be used again. **

[Write your answer here. Discuss specific concepts like thread creation, thread states, how threads execute concurrently, what surprised you, etc.]

---

## Question 2: What was the most challenging part of this assignment?

**Your Answer  The most challenging aspect was ensuring that Feature 3's waiting time calculation was accurate. Because I forgot to reset the timer each time a process returned to the queue, my waiting time numbers were initially far too high. Because a new thread entry is added to the map each time a process re-enters the queue, another issue was that the summary table displayed the same process multiple times. I had to carefully consider when the waiting period should begin and end. I had to follow the program step-by-step in order to locate these two errors, which were difficult to identify simply by reading the code. :**

[Describe the specific challenge. Was it understanding the code? Implementing a feature? Using Git? Explain what made it difficult and how it relates to the course concepts.]

---

## Question 3: How did you overcome the challenges you faced?

**Your Answer:   I started by carefully reading the code again to determine the exact position of each error. In order to examine what numbers the program was giving me regarding the waiting time issue, I put print statements in several locations. And then compared those numbers to my expectations. After identifying the source of the incorrect values, I adjusted the timer such that it resets each time a process returns to the queue. I just kept a record of process names that had already been printed and skipped them if they reappeared in order to solve the repeated rows issue. Overall, I was able to address both issues without becoming confused by closely examining the code and testing minor modifications one at a time. **

[Describe your problem-solving approach. Did you read documentation? Ask for help? Debug systematically? What resources did you use? What strategies worked?]

---

## Question 4: How can you apply multithreading concepts in real-world applications?

**Your Answer: Almost every application we use on a daily basis uses threads. Similar to how P6 finished our simulation quickly without waiting for the longer P3, each user request is processed by a separate thread in a web server, so one slow request does not prevent others from being executed. In a video player, the video is played concurrently by one thread, the audio is handled by another, and the next section is loaded from the internet by a third thread. To keep the screen responsive when you tap it, background processes on a smartphone, such as downloading updates, operate in different threads. These are all actual instances of the same idea that we developed for this assignment.  **

[Give specific examples from real applications you use (web browsers, games, mobile apps, etc.). Explain why threads are useful in those scenarios. Connect to what you learned in this assignment.]

---

## Additional Reflections (Optional)

### What would you like to learn more about?

[Any topics related to threading, concurrency, or operating systems that you're curious about?]

---

### How confident do you feel about multithreading concepts now?
  I am confident in my ability to create threads, understand the thread lifecycle, and describe Round-Robin scheduling. I still need more practice with more complex topics, such as protecting shared data between threads, since our simulation used join() to only let one thread to execute at a time.

[Explain your rating - what do you understand well? What needs more practice?]

---

### Feedback on the assignment

[Any comments about the assignment? Was it helpful? Too easy/hard? Suggestions for improvement?]

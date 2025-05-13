## 📘 **Unit 2: Process Scheduling and Synchronization**

---

## 🔹 **Part A: Process Scheduling**

---

### 🔸 1. **Process**

A **process** is a program in execution. It includes:

- Program counter
    
- Stack
    
- Data section
    
- Registers
    

---

### 🔸 2. **Process States**

1. **New** – process is being created.
    
2. **Ready** – waiting to be assigned to CPU.
    
3. **Running** – instructions are being executed.
    
4. **Waiting** – waiting for some event.
    
5. **Terminated** – process has finished execution.
    

---

### 🔸 3. **Scheduler Types**

| Scheduler Type                           | Role                                                           |
| ---------------------------------------- | -------------------------------------------------------------- |
| **Long-term Scheduler**                  | Selects which processes are admitted to system for processing. |
| **Short-term Scheduler (CPU Scheduler)** | Selects among ready processes for execution.                   |
| **Medium-term Scheduler**                | Temporarily removes processes from memory (swapping).          |

---

### 🔸 4. **CPU Scheduling**

Occurs when CPU switches from one process to another.

#### **Scheduling Criteria:**

- CPU Utilization
    
- Throughput
    
- Turnaround Time
    
- Waiting Time
    
- Response Time
    
- Fairness

### 🔸 5. **CPU Scheduling Algorithms**

---

#### ✅ **1. First-Come First-Serve (FCFS)**

- Simple and non-preemptive.
    
- Process executed in order of arrival.
    

📌 **Drawback**: Convoy effect – long processes delay shorter ones.

---

#### ✅ **2. Shortest Job First (SJF)**

- Selects process with shortest burst time.
    
- Optimal for minimizing average waiting time.
    

📌 **Types**:

- **Non-preemptive**
    
- **Preemptive (SRTF - Shortest Remaining Time First)**
    

---

#### ✅ **3. Priority Scheduling**

- Process with highest priority is scheduled first.
    
- Can be **preemptive** or **non-preemptive**.
    

📌 **Issue**: Starvation — low priority processes may never execute.

🛠 **Solution**: Aging (increase priority over time).

---

#### ✅ **4. Round Robin (RR)**

- Each process gets a fixed **time quantum**.
    
- Preemptive.
    

✅ Good for time-sharing systems.

📌 **Key Factor**: Choosing an optimal time quantum.

---

#### ✅ **5. Multilevel Queue Scheduling**

- Ready queue is split into multiple levels (foreground, background).
    
- Each queue has its own scheduling algorithm.
    
- Processes don’t move between queues.
    

---

#### ✅ **6. Multilevel Feedback Queue Scheduling**

- Like multilevel queue but **processes can move between queues** based on behavior and age.
    

---

#### ✅ **7. Real-Time Scheduling**

- For systems with strict timing constraints.
    

📌 **Types**:

- **Hard Real-Time**: Must meet deadlines.
    
- **Soft Real-Time**: Preferable to meet deadlines.
    

🧠 Algorithms: Rate Monotonic, Earliest Deadline First (EDF)

---

### 🔸 6. **Context Switching**

- Switching CPU from one process to another.
    
- OS saves the state of old process and loads the state of new process.
    
- Introduces overhead (no useful work is done).
    

---

## 🔹 **Part B: Process Synchronization**

---

### 🔸 1. **Why Synchronization?**

In a multiprogramming system, multiple processes access shared resources. **Process Synchronization** is needed to avoid inconsistencies and **race conditions**.

---

### 🔸 2. **Critical Section Problem**

A **critical section** is a code segment where a shared resource is accessed.

#### **Conditions to Solve It (3 Rules):**

1. **Mutual Exclusion** – Only one process in critical section.
    
2. **Progress** – If no process is in CS, one of the waiting ones should enter.
    
3. **Bounded Waiting** – Limit the number of times others can enter CS before one can re-enter.
    

---

### 🔸 3. **Software Solutions**

#### ✅ **Peterson’s Algorithm** (for two processes):

Uses two variables:

- `flag[2]` – intent to enter CS
    
- `turn` – whose turn it is
    

✅ Ensures mutual exclusion and bounded waiting.

---

#### ✅ **Bakery Algorithm**

- Suitable for **n processes**
    
- Processes take a "number" and enter CS based on lowest number.
    

---

### 🔸 4. **Hardware Solutions**

#### ✅ **Interrupt Disabling**

- Disable interrupts while in critical section.

📌 Not suitable for multiprocessor systems.

#### ✅ **Test and Set Instruction**

Atomic instruction used to implement locking.

---

### 🔸 5. **Semaphores**

A **synchronization tool** to manage access to shared resources.

#### **Types**:

- **Binary Semaphore**: 0 or 1 (mutex-like)
    
- **Counting Semaphore**: Integer value ≥ 0
    

#### **Operations**:

- `wait(S)` or `P(S)` → decrease semaphore, block if < 0
    
- `signal(S)` or `V(S)` → increase semaphore, wake waiting process
    

---

### 🔸 6. **Classical Synchronization Problems**

#### ✅ **1. Bounded Buffer (Producer-Consumer)**

- Producer adds, consumer removes.
    
- Use **mutex + full + empty semaphores**.
    

#### ✅ **2. Readers-Writers Problem**

- Multiple readers, one writer.
    
- Goal: Readers can access simultaneously, writers get exclusive access.
    

#### ✅ **3. Dining Philosophers**

- N philosophers sharing forks.
    
- Risk of deadlock and starvation.
    

---

### 🔸 7. **Monitors**

High-level synchronization construct that ensures only one process is active in monitor at a time.

✅ Language-supported solution (Java/C++ uses similar idea).

---

Let me know if you want:

- Short notes / summaries
    
- Diagrams or flowcharts for algorithms
    
- Pseudocode for scheduling or synchronization algorithms
    

I can also help with writing expected answers in your university exam style!
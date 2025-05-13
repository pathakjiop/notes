Here are **detailed exam-focused notes** for **Unit 1 – Introduction to Operating Systems (4IT03)** based on your uploaded PDF and your handwritten notes:

---

# 📘 **UNIT 1: INTRODUCTION TO OPERATING SYSTEM**

---

## 1️⃣ What is an Operating System?

- **Definition**: A system software that acts as a **bridge between user and hardware**, managing resources and enabling program execution.
    
- **Goals**:
    
    - **Convenience**: Easy for users to interact with computers.
        
    - **Efficiency**: Optimal use of hardware resources.
        
    - **Ability to Evolve**: Adaptability for new software/hardware developments.
        
- **Roles**:
    
    - **Resource Allocator**: Manages CPU, memory, I/O, etc.
        
    - **Control Program**: Supervises program execution to prevent errors and misuse.
        
- **Example**: Windows, Linux, MacOS.
    

---

## 2️⃣ Computer System Structure

- **Four Main Components**:
    
    1. **Hardware**: CPU, Memory, I/O devices.
        
    2. **Operating System**: Manages hardware.
        
    3. **Application Programs**: Word processors, browsers, games.
        
    4. **Users**: People, systems, machines.
        
- **Viewpoints**:
    
    - **Users**: Want speed and simplicity.
        
    - **Mainframes**: Must support multiple users.
        
    - **Embedded Systems**: Minimal or no user interaction.
        
    - **Handheld Devices**: Limited resources → optimized for battery and usability.
        

---

## 3️⃣ Evolution of Operating Systems

### 🔹 1. Serial Processing (1950s)

- No OS; user manually interacted with hardware.
    
- Time-consuming, error-prone.
    

### 🔹 2. Batch Processing

- Jobs grouped and processed sequentially.
    
- Reduces manual intervention, but CPU idle during I/O.
    

### 🔹 3. Multiprogramming

- Multiple jobs in memory → CPU switches between them.
    
- Improves CPU utilization.
    

### 🔹 4. Time Sharing (Multitasking)

- CPU divided into time slices → interactive user sessions.
    
- Enables simultaneous user programs.
    

### 🔹 5. Parallel Systems

- Multiple CPUs sharing memory/bus.
    
- Types: **Asymmetric** (one master), **Symmetric** (equal CPUs).
    
- High throughput, fault-tolerant.
    

### 🔹 6. Distributed Systems

- Multiple independent systems connected by network.
    
- Share resources, improve reliability.
    

### 🔹 7. Desktop Systems

- Personal computers (PCs).
    
- Prioritize user convenience over CPU utilization.
    

### 🔹 8. Real-Time Systems

- **Hard Real-Time**: Strict timing (e.g., medical, automotive).
    
- **Soft Real-Time**: Tolerant to delays (e.g., video streaming).
    

### 🔹 9. Handheld Systems

- PDAs, smartphones.
    
- Issues: low memory, slow CPUs, small screens.
    

---

## 4️⃣ Operating System Components

### 🔸 1. Process Management

- **Process**: Program in execution.
    
- Responsibilities:
    
    - Process creation, execution, termination.
        
    - Scheduling, synchronization, deadlock prevention.
        
    - Interprocess communication.
        

### 🔸 2. Memory Management

- Tracks memory usage.
    
- Allocates/deallocates memory.
    
- Optimizes memory utilization.
    

### 🔸 3. File Management

- File creation/deletion, directory management.
    
- Access permissions and backup.
    

### 🔸 4. I/O Management

- Abstracts hardware complexities via drivers.
    
- Uses buffering, spooling, caching.
    

### 🔸 5. Secondary Storage Management

- Manages HDDs/SSDs.
    
- Handles allocation, defragmentation, bad blocks.
    

### 🔸 6. Protection & Security

- Authorizes access to resources.
    
- Enforces authentication, safeguards user data.
    

### 🔸 7. Networking

- Manages communication across systems.
    
- Uses protocols for consistency and security.
    

### 🔸 8. Command Interpreter

- CLI/Shell → interprets user commands into OS operations.
    

---

## 5️⃣ Operating System Services

|Service|Description|
|---|---|
|Program Execution|Loads, runs programs; manages processes.|
|I/O Operations|Manages input/output devices.|
|File System Manipulation|File creation, access, deletion.|
|Communication|Shared memory / Message passing between processes.|
|Error Detection|Detects/responds to hardware/software issues.|
|Resource Allocation|Allocates CPU, memory, devices.|
|Protection|Prevents unauthorized access to data/resources.|

---

## 6️⃣ Process Management

### 🔹 Process = Program in Execution

### 🔹 Process Structure:

- Text (code), Data, Stack, Heap, Program Counter, Registers.
    

### 🔹 Process States:

1. New
    
2. Ready
    
3. Running
    
4. Waiting
    
5. Terminated
    

### 🔹 Process Control Block (PCB):

Stores process metadata: state, PC, memory, I/O, etc.

### 🔹 Scheduling:

- **Schedulers**:
    
    - Long-Term (Job Scheduler)
        
    - Short-Term (CPU Scheduler)
        
    - Medium-Term (Swapper)
        
- **Queues**:
    
    - Job Queue
        
    - Ready Queue
        
    - I/O Queue
        

### 🔹 Context Switching:

- Saves/restores process states.
    
- Causes overhead (no work during switch).
    

### 🔹 Process Creation:

- **fork()** → creates a new process.
    
- **exec()** → replaces process memory with new program.
    

### 🔹 Termination:

- Upon completion or error.
    
- May trigger **cascading termination** of child processes.
    

---

## 7️⃣ Interprocess Communication (IPC)

### 🔹 Process Types:

- **Independent**: No interaction.
    
- **Cooperating**: Share info/resources.
    

### 🔹 IPC Models:

1. **Shared Memory**: Fast, used for performance-critical systems.
    
2. **Message Passing**: Easier for distributed systems.
    

### 🔹 Message Passing Details:

#### ✅ Direct Communication:

- `send(P1, msg)` / `receive(P1, msg)`
    
- Requires known process ID.
    

#### ✅ Indirect Communication:

- Uses **mailboxes** (ports) instead of process IDs.
    
- `send(mailbox, msg)` / `receive(mailbox, msg)`
    

### 🔹 Mailbox Sharing Issues:

- If multiple receivers exist, who gets the message?
    
    - Solutions:
        
        - Limit to 2 processes
            
        - One receiver at a time
            
        - Let OS choose arbitrarily
            

### 🔹 Synchronization:

- **Blocking** (Synchronous): Waits until communication completes.
    
- **Non-blocking** (Asynchronous): Continues without waiting.
    

### 🔹 Buffering:

1. **Zero Capacity**: Sender waits (rendezvous).
    
2. **Bounded Capacity**: Waits if full.
    
3. **Unbounded**: Never waits.
    

---

## 8️⃣ Producer-Consumer Problem

- A classic **cooperation problem** using shared buffer.
    
- Producer adds items to buffer, Consumer removes items.
    
- Must avoid race conditions using synchronization mechanisms.
    

---

Let me know if you'd like this in a **PDF or Word format**, or if you'd like visual **diagrams** for concepts like Process State or Scheduling Queues.
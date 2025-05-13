## 📘 **Unit 4: Virtual Memory**

---

### 🔸 1. **What is Virtual Memory?**

**Virtual Memory** is a memory management technique that:

- Gives an **illusion of a large memory** to users by using disk space.
    
- Allows execution of processes **not completely in main memory**.
    
- Separates **logical memory** from **physical memory**.
    

🧠 **Purpose**:

- Efficient memory utilization
    
- Allows **multiprogramming**
    
- Reduces program loading time
    

---

### 🔸 2. **Advantages of Virtual Memory**

- Programs can be **larger than physical memory**.
    
- More processes can be kept in memory → **better CPU utilization**.
    
- Facilitates **process isolation** and protection.
    
- **Simplifies loading and linking**.
    

---

### 🔸 3. **Demand Paging**

In **demand paging**, pages are brought into memory **only when required**, not all at once.

#### 🔹 Components:

- **Page Table**: Maps logical pages to frames.
    
- **Valid/Invalid Bit**:
    
    - Valid → Page in memory
        
    - Invalid → Page on disk (or not allocated)
        

#### 🔹 Page Fault:

Occurs when the page is **not in memory** → triggers:

1. Trap to OS
    
2. OS finds page on disk
    
3. OS finds free frame
    
4. Loads page into frame
    
5. Updates page table
    
6. Restarts instruction
    

---

### 🔸 4. **Page Replacement**

If memory is full, we must replace a page to bring in a new one.

#### 🔹 Page Replacement Algorithms:

1. **FIFO (First In First Out)**
    
    - Oldest page is replaced.
        
    - Simple, but may remove useful pages.
        
2. **LRU (Least Recently Used)**
    
    - Replaces page not used for longest time.
        
    - More accurate but needs hardware support.
        
3. **Optimal**
    
    - Replaces page that will **not be used for longest time** in future.
        
    - Ideal but not practical.
        

🧠 **Belady's Anomaly**: In FIFO, increasing number of frames can increase page faults!

---

### 🔸 5. **Performance of Demand Paging**

Let:

- **p** = probability of page fault
    
- **ma** = memory access time
    
- **pf** = page fault service time
    

**Effective Access Time (EAT)** =  `(1 – p) × ma + p × pf`

💡 Page faults must be **rare** for EAT to be close to `ma`.

---

### 🔸 6. **Thrashing**

When a process spends **more time handling page faults** than executing, it's called **thrashing**.

#### 🔹 Causes:

- Too many processes
    
- Insufficient frames per process
    

#### 🔹 Effects:

- High page-fault rate
    
- Low CPU utilization
    

#### 🔹 Solutions:

- Use **Local Replacement** instead of Global
    
- **Working Set Model** (discussed below)
    
- **Load Control**: Reduce degree of multiprogramming
    

---

### 🔸 7. **Allocating Frames**

#### 🔹 Strategies:

1. **Equal Allocation**: Each process gets equal number of frames.
    
2. **Proportional Allocation**: Based on process size.
    
3. **Global vs Local**:
    
    - **Global**: A process can take frames from others.
        
    - **Local**: Process can only use its allocated frames.
        

---

### 🔸 8. **Working Set Model**

Defines the **working set** `W(t, Δ)` of a process at time `t` as the set of pages used during the last `Δ` time units.

🔸 Goals:

- Keep the working set in memory
    
- Prevent thrashing
    

#### 🔹 Working Set Policy:

- Monitor working set
    
- Ensure it fits in available memory
    

---

### 🔸 9. **Page Fault Frequency (PFF) Scheme**

Adjusts memory allocation by monitoring the **frequency of page faults**.

- High page fault rate → Allocate more frames
    
- Low page fault rate → Reclaim frames
    

🧠 Helps maintain balance between memory usage and performance.

---

### 🔸 10. **Memory-Mapped Files**

Uses virtual memory techniques to map disk files into memory space for fast file I/O.

- Efficient for accessing large files.
    
- Common in OS like Windows and Unix.
    

---

### 🔸 11. **Copy-on-Write (COW)**

Optimization used in **process creation (fork)**:

- Parent and child share pages in memory initially.
    
- Pages are copied **only when modified**.
    

✅ Saves memory  
✅ Speeds up process creation

---

### 🔸 12. **Other Key Concepts**

#### 🔹 Inverted Page Table:

- One entry per **frame**, not per page.
    
- Reduces memory used for page tables in large address spaces.
    

#### 🔹 TLB (Translation Lookaside Buffer):

- A cache for page table entries.
    
- Reduces address translation time.
    

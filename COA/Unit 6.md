**UNIT 6: MEMORY ORGANIZATION - DETAILED NOTES**

---

### 1. MEMORY HIERARCHY

- Organized to balance speed, cost, and size.
    
- **Levels (top to bottom):**
    
    - Registers (fastest, smallest)
        
    - Cache Memory
        
    - Main Memory (RAM)
        
    - Secondary Storage (Hard Disk, SSD)
        
    - Backup Storage (CD/DVD, Tape)
        

#### Characteristics:

- **Access Time**: Time to read/write.
    
- **Memory Cost**: Cost per bit.
    
- **Capacity**: Amount of data stored.
    

---

### 2. MAIN MEMORY ORGANIZATION

- Also known as **RAM** (Random Access Memory).
    
- Stores data and instructions currently in use.
    

#### Types:

- **SRAM** (Static RAM): Faster, expensive, used in cache.
    
- **DRAM** (Dynamic RAM): Slower, cheaper, used in main memory.
    

#### Memory Cell:

- Made of flip-flops or transistors.
    

---

### 3. CACHE MEMORY

- Small, fast memory between CPU and RAM.
    
- Stores recently used data.
    

#### Working:

- **Hit**: Data found in cache.
    
- **Miss**: Data not found → load from RAM.
    

#### Mapping Techniques:

1. **Direct Mapping**:
    
    - Each block maps to only one cache line.
        
    - Simple but may lead to frequent replacement.
        
2. **Associative Mapping**:
    
    - Any block can go into any line.
        
    - More flexible but requires more hardware.
        
3. **Set-Associative Mapping**:
    
    - Cache is divided into sets.
        
    - Block can go into any line within the set.
        

#### Replacement Policies:

- **LRU** (Least Recently Used)
    
- **FIFO** (First-In First-Out)
    

#### Write Policies:

- **Write-through**: Updates cache and memory simultaneously.
    
- **Write-back**: Updates only cache, writes to memory later.
    

---

### 4. VIRTUAL MEMORY

- Technique to use more memory than physically available.
    
- Uses **disk space** as extension of RAM.
    

#### Components:

- **Page Table**: Maps virtual addresses to physical addresses.
    
- **TLB (Translation Lookaside Buffer)**: Fast access to page table entries.
    

#### Techniques:

1. **Paging**:
    
    - Memory is divided into fixed-size pages.
        
    - Virtual address → page number + offset.
        
2. **Segmentation**:
    
    - Memory is divided by logical segments (code, data, stack).
        
    - Address → segment number + offset.
        

---

### 5. MEMORY MANAGEMENT HARDWARE

- **MMU (Memory Management Unit)**: Hardware that handles address translation.
    
- **Address Binding**:
    
    - Compile-time, load-time, or run-time.
        

---

### 6. AUXILIARY MEMORY

- Used for **non-volatile** long-term storage.
    
- Examples: Hard Disk, SSD, Magnetic Tape.
    
- Slower but high capacity and cheaper.
    

#### Disk Access Time:

- **Seek Time**: Time to position head over track.
    
- **Rotational Latency**: Time for desired sector to rotate under head.
    
- **Transfer Time**: Time to read/write the sector.
    

---

### 7. MEMORY PROTECTION & MANAGEMENT

#### Protection:

- Prevents a process from accessing unauthorized memory.
    
- Achieved using **base and limit registers** or **segmentation hardware**.
    

#### Management:

- OS keeps track of memory allocation.
    
- Swapping, fragmentation management.
    

---

### 8. EXAM PREPARATION TIPS

- Be able to compare **mapping techniques in cache**.
    
- Learn **paging vs segmentation** with diagrams.
    
- Practice numerical problems on **hit/miss ratio, access time**.
    
- Draw and label **cache structure, MMU, page table**.
    
- Understand **virtual memory implementation and role of TLB**.
    

---

This concludes the full in-detailed notes for **UNIT 6: Memory Organization**.
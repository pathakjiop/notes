
## 🚀 1. **Why Cache Memory?**

- Processor is **much faster** than main memory.
    
- Processor spends time **waiting** for data from memory.
    
- Cache is a small, fast memory that stores **frequently accessed data**.
    
- Based on the **principle of locality**:
    
    - **Temporal locality**: Recently accessed data is likely to be accessed again soon.
        
    - **Spatial locality**: Nearby data addresses are likely to be used soon.
        

---

## 📥 2. **Cache Operations**

### ✅ Cache Hit:

- Data found in cache.
    
- Read hit: Use cached data.
    
- Write hit:
    
    - **Write-through**: Update both cache and memory.
        
    - **Write-back**: Update cache only, mark dirty. Memory updated when block is replaced.
        

### ❌ Cache Miss:

- Data not in cache.
    
- **Read miss**: Load block from memory to cache.
    
- **Write miss**:
    
    - Write-through: Directly update memory.
        
    - Write-back: Load block to cache, update it.
        
- **Load-through / early restart**: Processor gets word before full block transfer completes.
    

---

## 🧭 3. **Mapping Techniques**

### 1. **Direct Mapping**

- Each memory block maps to a **specific cache block**.
    
- Uses **block number % cache size**.
    
- Simple but can cause frequent replacements.
    
- Address divided into: **Tag | Block | Word**
    

### 2. **Associative Mapping**

- Memory block can go to **any cache block**.
    
- Address split into: **Tag | Word**
    
- Requires **searching all cache tags** → More hardware cost, more flexible.
    

### 3. **Set-Associative Mapping**

- Cache divided into **sets** with multiple blocks per set.
    
- Memory block maps to a set.
    
- Address: **Tag | Set | Word**
    
- Combines benefits of direct and associative mapping.
    

---

## 📈 4. **Performance Factors**

- **Hit Rate**: Percentage of accesses found in cache.
    
- **Miss Penalty**: Time taken to fetch data from memory after a miss.
    
- **Improving hit rate**:
    
    - Increase block size (but not too big).
        
    - Use **load-through**.
        

### Cache on Processor Chip

- Modern CPUs have **multi-level caches**: L1 (smallest, fastest), L2.
    
- Access time: `Tavg = h1c1 + (1 - h1)h2c2 + (1 - h1)(1 - h2)M`
    

---

## 📚 5. **Other Cache Techniques**

### ✅ **Write Buffer**

- Temporarily holds write operations.
    
- Speeds up processor if it doesn't wait for memory write.
    

### ✅ **Prefetching**

- Loads data **before it’s needed**.
    
- Can be done in **software** or **hardware**.
    

### ✅ **Lockup-Free Cache**

- Allows other accesses during a cache miss.
    
- Uses special registers to track multiple outstanding misses.
    

---

## 💾 6. **Virtual Memory**

- Used to simulate a **larger memory space** than physically available.
    
- **Parts of program** are loaded into memory **only when needed**.
    

### Virtual vs Physical Address

- **Virtual address**: Issued by processor.
    
- **Physical address**: Used to access main memory.
    
- **MMU (Memory Management Unit)** translates virtual → physical.
    

### Page Table

- Virtual address = **Page Number + Offset**
    
- Page table maps page number to **frame number**.
    
- Stored in main memory, base address in **PTBR (Page Table Base Register)**.
    

### Translation Lookaside Buffer (TLB)

- A **cache for page table entries**.
    
- Speeds up address translation.
    

### Page Fault

- Occurs when page is not in main memory.
    
- OS loads page from disk → memory → resumes execution.
    

---

## 🔁 7. **Page Replacement & Management**

- When memory is full, an existing page must be replaced.
    
- Uses **LRU (Least Recently Used)** or similar algorithms.
    
- Pages marked with **valid** and **modified (dirty)** bits.
    
- Similar to cache replacement.
    

---

## 🔐 8. **Protection & Management**

- **User vs Supervisor state**:
    
    - User programs can't change page tables.
        
    - Privileged instructions for OS only.
        
- Each process gets **separate virtual space**.
    
- **Page Table switching** enables context switching between processes.
    

---

Let me know if you want a compact one-pager or flashcards for revision!
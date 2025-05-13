## ✅ **UNIT 6 – I/O SYSTEMS AND DISK SCHEDULING**

---

### 🔹 **1. I/O Systems Overview**

- I/O = Input/Output, handles communication between system and external devices.
    
- Three main layers:
    
    - **Application I/O Interface**
        
    - **Kernel I/O Subsystem**
        
    - **Hardware Layer**
        

---

### 🔹 **2. I/O Hardware**

- Devices vary (keyboard, disk, mouse) but share:
    
    - **Ports:** Connection points for I/O devices.
        
    - **Bus:** Path for data transfer.
        
    - **Controller:** Device-specific communication handler.
        

---

### 🔹 **3. Communication Techniques**

- **Polling:** CPU checks device status repeatedly.
    
- **Interrupts:** Device notifies CPU when ready.
    
- **DMA (Direct Memory Access):**
    
    - Transfers data directly between memory and device (bypasses CPU).
        
    - Efficient for large data.
        

---

### 🔹 **4. Types of Devices**

- **Character Devices:** Keyboard, mouse – handled byte by byte.
    
- **Block Devices:** Disks – handled block by block.
    
- **Network Devices:** Handled via sockets.
    

---

### 🔹 **5. I/O Methods**

|Type|Description|
|---|---|
|**Blocking**|Process waits until I/O is done.|
|**Non-blocking**|Process continues and checks later.|
|**Asynchronous**|Process is notified when I/O completes.|

---

### 🔹 **6. Kernel I/O Subsystem Functions**

- **Scheduling:** Prioritize I/O requests.
    
- **Buffering:** Temporary storage to match speed differences.
    
- **Caching:** Store copies of data for faster access.
    
- **Spooling:** Queue output (e.g., printing).
    
- **Device Reservation:** Prevents conflict when multiple processes use a device.
    

---

### 🔹 **7. Error Handling & Protection**

- **Error Handling:** Detects and recovers from device failures.
    
- **I/O Protection:** Prevents direct access to devices – all I/O through system calls.
    

---

### 🔹 **8. STREAMS (UNIX Specific)**

- Full-duplex channels between user and device.
    
- Made of queues (read/write) for communication.
    

---

### 🔹 **9. Disk Scheduling Algorithms**

| Algorithm           | How it Works                                 | Notes                          |
| ------------------- | -------------------------------------------- | ------------------------------ |
| **FCFS**            | First-come-first-served                      | Simple but slow.               |
| **SSTF**            | Shortest seek time first                     | Faster, may cause starvation.  |
| **SCAN (Elevator)** | Moves head in one direction, then reverses   | Balanced.                      |
| **C-SCAN**          | Like SCAN, but always moves in one direction | Better wait time distribution. |
| **LOOK**            | Like SCAN but goes only as far as needed     | Optimized SCAN.                |
| **C-LOOK**          | Like C-SCAN but avoids going to end          | Optimized C-SCAN.              |

---

### 🔹 **10. Performance Factors**

- Reduce:
    
    - Context switches
        
    - Data copying
        
    - Interrupts
        
- Use:
    
    - Smart controllers
        
    - Large data transfers
        
    - DMA
        

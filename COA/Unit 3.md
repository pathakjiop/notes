## 🔵 1. Introduction: The Need for Input/Output (I/O)

- **Basic Feature of Computer**:
    
    - Ability to **exchange data** with outside world (users, other systems, environment).
        
- **Examples of Input and Output**:
    
    ||Examples|
    |:--|:--|
    |**Input**|Keyboard, sensor switches, digital cameras, microphones, fire alarms.|
    |**Output**|Display screens, speakers, digitally coded commands to other systems.|
    
- **Direct Use of Computers**:
    
    - Communication with other computers over the Internet.
        
- **Indirect Use**:
    
    - Embedded in home appliances, transport systems, banking terminals, manufacturing.
        
- **Challenge**:
    
    - Computers must interface with **a wide variety of devices** operating under **different conditions and speeds**.
        

---

## 🔵 2. Accessing I/O Devices

- **Single Bus Structure**:
    
    - I/O devices and memory share the same **address**, **data**, and **control** lines on a bus.
        
- **Process**:
    
    1. Processor places the address on address lines.
        
    2. Device detects address (via **Address Decoder**).
        
    3. Processor sends control signals (Read/Write).
        
    4. Data transferred over data lines.
        

### 2.1 Addressing I/O Devices

|Addressing Mode|Description|
|:--|:--|
|**Memory-Mapped I/O**|Devices share the memory address space. Regular memory instructions (like LOAD, STORE) can access I/O. Simplifies software.|
|**Isolated I/O (Separate I/O)**|Devices have a separate address space. Special I/O instructions are needed. Saves address space.|

---

## 🔵 3. I/O Interface Circuit

Each device connects through an **I/O Interface** that includes:

|Component|Purpose|
|:--|:--|
|**Address Decoder**|Detects its own address on bus.|
|**Control Circuit**|Coordinates I/O activities.|
|**Data Register**|Holds data for transfer to/from processor.|
|**Status Register**|Holds status info like "Ready" or "Busy".|

🧠 **Tip**:  
I/O interface **translates** CPU operations into device actions.

---

## 🔵 4. Synchronizing Data Transfers (CPU vs. I/O Speed Mismatch)

- **Problem**: CPU operates much faster than I/O devices.
    
- **Solutions**:
    
    1. **Program-Controlled I/O**:
        
        - CPU continuously checks device status (polling).
            
        - Very inefficient (CPU wastes time).
            
    2. **Interrupts**:
        
        - Device interrupts CPU when ready.
            
        - CPU can perform useful work meanwhile.
            
    3. **Direct Memory Access (DMA)**:
        
        - Device directly transfers data to/from memory without CPU involvement.
            

---

# 🔵 5. INTERRUPTS

---

### 5.1 What is an Interrupt?

- A **hardware signal** from a device that **alerts the processor** when the device is ready.
    
- **Dedicated bus line**: Interrupt Request (IRQ).
    
- **Interrupt Service Routine (ISR)**:
    
    - Special program that handles the interrupt.
        
    - CPU saves its context (PC, registers), jumps to ISR, then resumes normal program.
        

---

### 5.2 Steps in Interrupt Handling

1. CPU completes current instruction.
    
2. Saves PC + Processor Status (condition codes).
    
3. Branches to ISR (Interrupt Service Routine).
    
4. ISR services device, restores CPU context.
    
5. Returns to main program execution.
    

---

### 5.3 Interrupt vs Subroutine Call

| Aspect | Interrupt | Subroutine | |:--|:--| | Purpose | External event-driven | Program logic-driven | | Initiation | By hardware | By program code | | Save/Restore | Full context save required | Minimal save (return address only) |

---

### 5.4 Interrupt Latency

- **Definition**: Time delay between **interrupt request** and **start of ISR**.
    
- **Cause**: Saving CPU state to memory.
    
- **Optimization**:
    
    - Save only **minimal registers** automatically.
        
    - Save rest inside ISR manually if needed.
        

---

### 5.5 Interrupt Acknowledgement

- CPU must **acknowledge** device after receiving interrupt.
    
- Methods:
    
    - Dedicated **acknowledge signal**.
        
    - Completion of data transfer as implicit acknowledgement.
        

---

### 5.6 Enabling and Disabling Interrupts

- **Instructions available** to enable/disable interrupts.
    
- Use case:
    
    - Prevent nested interrupts while ISR is executing.
        
- Common practice:
    
    - Disable at ISR start, enable before ISR end.
        

---

## 🔵 6. Handling Multiple Devices

### 6.1 Problem Statement

- Multiple devices may send interrupts.
    
- CPU must identify:
    
    1. Which device sent the interrupt?
        
    2. Which ISR to run?
        

---

### 6.2 Methods to Identify Devices

|Method|Explanation|
|:--|:--|
|**Polling**|CPU checks status of each device one-by-one. (Simple but slow)|
|**Vectored Interrupts**|Device sends its ID/code with interrupt. CPU jumps directly to device-specific ISR. (Faster)|

---

### 6.3 Priority of Interrupts

- **Simple Priority**: High-speed devices (e.g., disks) get priority over slow devices (e.g., keyboard).
    
- CPU has **priority register** to maintain and compare priority levels.
    

---

### 6.4 Interrupt Nesting

- A high-priority interrupt can interrupt the servicing of a lower-priority interrupt.
    

🧠 Example:  
Keyboard interrupt (lower priority) can be interrupted by Disk interrupt (higher priority).

---

### 6.5 Privilege Levels

- Only **supervisor mode** can execute privileged instructions (changing priorities, controlling hardware).
    
- **Privilege Exception**: Occurs when user mode tries privileged actions.
    

---

## 🔵 7. Direct Memory Access (DMA)

- **Problem**: CPU wasting time moving large data blocks (disk, network).
    
- **Solution**:
    
    - **DMA Controller** handles memory <-> I/O transfer independently.
        
    - CPU configures DMA once, and continues other tasks.
        

### 7.1 DMA Working Steps

1. CPU provides:
    
    - Start memory address
        
    - Word count
        
    - Direction (read/write)
        
2. DMA controller transfers data directly.
    
3. On completion, DMA interrupts CPU.
    

---

### 7.2 Cycle Stealing vs Burst Mode

|Mode|Description|
|:--|:--|
|**Cycle Stealing**|DMA takes one bus cycle at a time, CPU waits temporarily.|
|**Burst Mode**|DMA locks bus and transfers full block at once. CPU paused longer.|

---

## 🔵 8. Bus Arbitration

### 8.1 Centralized Arbitration

- Single **Bus Arbiter** decides who controls the bus (CPU or DMA).
    
- Common signals:
    
    - **BR** (Bus Request)
        
    - **BG** (Bus Grant)
        
    - **BBSY** (Bus Busy)
        

### 8.2 Distributed Arbitration

- No central controller.
    
- Devices coordinate among themselves based on 4-bit ID numbers using logical OR on bus lines.
    
- More fault tolerant.
    

---

## 🔵 9. Bus Structures and Protocols

- **Bus Types**:
    
    |Type|Lines|
    |:--|:--|
    |Data Bus|Transfer of actual data.|
    |Address Bus|Specify memory or device address.|
    |Control Bus|Control signals (read, write, interrupt).|
    
- **Bus Protocol**:
    
    - Set of rules defining communication over the bus.
        

---

## 🔵 10. Bus Timing

|Timing Type|Explanation|
|:--|:--|
|**Synchronous Bus**|Bus clock synchronizes all devices. Faster, but all devices must match speed.|
|**Asynchronous Bus**|Handshake signals (`Master-ready`, `Slave-ready`) coordinate transfer. Supports varied device speeds.|

---

### 10.1 Timing Diagrams

- **Synchronous Bus Timing**:  
    Fixed intervals between address, command, data, and acknowledgement.
    
- **Asynchronous Bus Timing**:  
    Master and slave handshake flexibly before/after transfer.
    

---

## 🔵 11. Summary of Important Points

|Topic|Key Points|
|:--|:--|
|Program-Controlled I/O|Polling device status.|
|Interrupt I/O|Device interrupts CPU.|
|DMA|Device transfers directly to memory.|
|Arbitration|Centralized or Distributed selection of bus master.|
|Bus Timing|Synchronous (clocked) vs Asynchronous (handshake based).|


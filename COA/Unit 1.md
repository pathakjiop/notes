## 🔵 1. INTRODUCTION TO COMPUTER SYSTEMS

### 1.1 What is a Computer?

- **Computer** = An advanced electronic machine that:
    
    - Accepts **input information**.
        
    - **Processes** input based on **internally stored instructions** (Program).
        
    - **Generates output** for users or other systems.
        
- **Program** = List of instructions.
    
- **Memory** = Internal storage where program and data reside.
    

---

### 1.2 Components:

|Part|Description|
|:--|:--|
|**Input Devices**|Keyboard, mouse, microphone.|
|**Output Devices**|Monitor, printer, speakers.|
|**Processor (CPU)**|Executes programs; includes ALU, Control Unit, Registers.|
|**Memory**|Stores data/instructions (RAM, ROM, Cache).|
|**I/O Controllers**|Interfaces for devices (disks, network).|

---

## 🔵 2. HARDWARE, ORGANIZATION, ARCHITECTURE

|Term|Meaning|
|:--|:--|
|**Hardware**|Physical parts — circuits, cables, display, storage.|
|**Computer Organization**|How hardware operates and interacts internally.|
|**Computer Architecture**|The logical design — instruction set, addressing, data types. (What software "sees")|

🧠 **Tip:**

- _Organization_ = Implementation.
    
- _Architecture_ = Design blueprint.
    

---

## 🔵 3. TYPES OF COMPUTERS

|Type|Characteristics|
|:--|:--|
|**Personal Computer (PC)**|For single users, moderate speed.|
|**Notebook / Laptop**|Portable, lightweight.|
|**Workstation**|High computing power, graphical tasks.|
|**Mainframe**|Large, reliable, supports hundreds of users.|
|**Supercomputer**|Extreme speed, scientific simulations.|

- **Comparison factors**: Size, Speed, Cost, Performance.
    

---

## 🔵 4. FUNCTIONS OF A COMPUTER

Four Basic Functions:

1. **Input**: Accept information (from user/devices).
    
2. **Memory Storage**: Save instructions and data.
    
3. **Processing**: Manipulate data according to program.
    
4. **Output**: Produce final results.
    

---

## 🔵 5. FUNCTIONAL UNITS (BLOCK DIAGRAM)

```
Input → Control Unit ↔ Memory ↔ ALU → Output
```

|Unit|Work|
|:--|:--|
|**Input Unit**|Takes input, converts to machine-readable format.|
|**Memory**|Stores data/instructions temporarily (RAM) or permanently (ROM).|
|**ALU (Arithmetic Logic Unit)**|Executes arithmetic (+, -, *, /) and logical (AND, OR) operations.|
|**Control Unit**|Directs all units, sends timing signals, manages instruction execution.|
|**Output Unit**|Converts processed data to human-readable form (Monitor/Printer).|

---

## 🔵 6. INFORMATION HANDLED

|Type|Meaning|
|:--|:--|
|**Instructions**|Control operations (fetch, decode, execute).|
|**Data**|Operands for instructions (numbers, text).|

- Both are encoded as **binary** (0,1).
    

---

## 🔵 7. BASIC OPERATIONAL CONCEPTS (INSTRUCTION CYCLE)

- **Fetch → Decode → Execute → Store**.
    

**Example:**

- `ADD LOC A, R0`
    
    - Fetch instruction (ADD).
        
    - Fetch operand at LOC A.
        
    - Add operand to Register R0.
        
    - Store result in R0.
        

|Register|Purpose|
|:--|:--|
|**IR (Instruction Register)**|Stores current instruction.|
|**PC (Program Counter)**|Holds next instruction address.|
|**MAR (Memory Address Register)**|Address to access memory.|
|**MDR (Memory Data Register)**|Data fetched from memory.|

---

## 🔵 8. INTERRUPT MECHANISM

- Devices raise **interrupts** to signal CPU.
    
- **Interrupt Service Routine (ISR)**:
    
    - Save current CPU state.
        
    - Perform service for the device.
        
    - Restore CPU state and resume execution.
        

---

## 🔵 9. BUS STRUCTURES

|Type|Characteristics|
|:--|:--|
|**Single Bus**|Only 1 transfer at a time, cheaper but slower.|
|**Multiple Bus**|Parallel transfers, expensive but faster.|

**Components on Bus**: CPU, Memory, I/O devices.

**Problem**: Devices have different speeds.

**Solution**: Use **buffer registers** to match speeds.

---

## 🔵 10. SOFTWARE

|Type|Description|
|:--|:--|
|**Application Software**|C, C++, Java programs (user-focused).|
|**System Software**|OS, Compilers, Assemblers (manage hardware).|

---

## 🔵 11. PERFORMANCE OF COMPUTER SYSTEM

**Important Factors**:

- Hardware efficiency.
    
- Instruction Set.
    
- Compiler quality.
    

**Performance Formula**:

```
T = (N × S) / R
```

- T = Execution time
    
- N = Instruction count
    
- S = Steps per instruction
    
- R = Clock rate
    

---

## 🔵 12. PIPELINING & SUPERSCALAR EXECUTION

- **Pipelining**:
    
    - Execute multiple instructions simultaneously at different stages.
        
- **Superscalar**:
    
    - Execute multiple instructions in parallel.
        

🧠 **Goal**: Maximize CPU utilization.

---

## 🔵 13. RISC vs CISC

|Feature|RISC|CISC|
|:--|:--|:--|
|Instruction Set|Simple, few instructions|Complex, many instructions|
|Focus|Speed through pipelining|Complex operations|
|Example|ARM, MIPS|x86|

---

# 🟡 MEMORY CONCEPTS

---

## 🔵 14. MEMORY LOCATIONS AND ADDRESSES

- **Bit**: Smallest storage unit (0 or 1).
    
- **Byte**: 8 bits.
    
- **Word**: 16, 32, 64 bits depending on architecture.
    
- **Address Space**:
    
    - 24-bit → 16M addresses.
        
    - 32-bit → 4G addresses.
        
- **Byte-addressable**: Each byte has a unique address.
    

---

## 🔵 15. BIG-ENDIAN vs LITTLE-ENDIAN

|Type|Meaning|
|:--|:--|
|Big-Endian|High-order byte stored at lowest address.|
|Little-Endian|Low-order byte stored at lowest address.|

---

## 🔵 16. MEMORY OPERATIONS

|Operation|Meaning|
|:--|:--|
|**Load** (Read)|Copy memory content to CPU.|
|**Store** (Write)|Copy CPU data to memory.|

---

# 🟡 INSTRUCTION FORMATS & SEQUENCING

---

## 🔵 17. CPU ORGANIZATION TYPES

|Organization|Meaning|
|:--|:--|
|Single Accumulator|Only one accumulator used.|
|General Register|Multiple registers used for operands.|
|Stack|Operands stored in a stack (LIFO).|

---

## 🔵 18. INSTRUCTION FORMATS

|Format|Example|
|:--|:--|
|Three-Address|`ADD R1, R2, R3`|
|Two-Address|`ADD R1, R2`|
|One-Address|`ADD A`|
|Zero-Address|Stack-based, no explicit operands.|
|RISC|Load/store architecture.|

---

## 🔵 19. PROGRAM SEQUENCING

- **Straight-Line**: Simple instruction sequence.
    
- **Branching**: Change of instruction flow.
    

---

## 🔵 20. CONDITION CODES (FLAGS)

|Flag|Meaning|
|:--|:--|
|N (Negative)|Result is negative.|
|Z (Zero)|Result is zero.|
|V (Overflow)|Overflow occurred.|
|C (Carry)|Carry/borrow occurred.|

---

# 🟡 ADDRESSING MODES

---

## 🔵 21. ADDRESSING MODES SUMMARY

|Mode|Description|
|:--|:--|
|Immediate|Operand in instruction.|
|Register|Operand in register.|
|Direct|Memory address given.|
|Indirect|Address contains operand address.|
|Autoincrement / Autodecrement|Register value updated after/before access.|
|Indexed|Operand address = base + index.|
|Relative|PC + offset to find address.|

🧠 **Tip:**

- _Immediate_ = Constant.
    
- _Direct_ = Address directly given.
    
- _Indirect_ = Address points to another address.
    

---

# 🟡 INPUT/OUTPUT OPERATIONS

---

## 🔵 22. BASIC I/O

- Devices need CPU interaction for data exchange.
    
- **Program-Controlled I/O**: CPU waits (wasteful).
    
- **Interrupt-driven I/O**: Efficient, CPU free for other tasks.
    
- **Memory-Mapped I/O**: I/O devices mapped into memory address space.
    

---

# 🟡 STACKS, QUEUES, AND SUBROUTINES

---

## 🔵 23. STACK

- **LIFO** structure.
    
- **Push**: Insert data.
    
- **Pop**: Remove data.
    
- **Memory Stack**: Stack implemented in RAM.
    

---

## 🔵 24. QUEUE

- **FIFO** structure.
    
- Requires **front** and **rear** pointers.
    
- **Circular Buffer** used to prevent memory overflow.
    

---

## 🔵 25. SUBROUTINES

|Term|Meaning|
|:--|:--|
|Call|Save current PC to Link Register and jump to subroutine.|
|Return|Restore PC from Link Register.|
|Stack Frame|Private workspace for subroutine parameters and local variables.|

**Parameter Passing**:

- By Value.
    
- By Reference.
    

---

# 🟡 HISTORICAL PERSPECTIVE

---

## 🔵 26. COMPUTER GENERATIONS

|Generation|Key Technology|Innovations|
|:--|:--|:--|
|1st (1945-1955)|Vacuum Tubes|Assembly language, Mercury delay memory.|
|2nd (1955-1965)|Transistors|High-level language (Fortran), Compilers.|
|3rd (1965-1975)|ICs (Integrated Circuits)|Cache memory, Virtual memory.|
|4th (1975-present)|VLSI (Very Large Scale Integration)|Microprocessors, PCs, LANs.|

## 🔵 1. Introduction: What is the Processing Unit?

- **Processing Unit** (Processor/CPU):
    
    - Fetches and executes machine instructions.
        
    - Coordinates activities of all other units (memory, input, output).
        
- **Execution Flow**:
    
    - Instructions are fetched **sequentially** from memory until a **branch/jump**.
        
    - Processor keeps track of the **next instruction address** using the **Program Counter (PC)**.
        
- Important Registers:
    
    |Register|Function|
    |:--|:--|
    |**Program Counter (PC)**|Holds the address of next instruction.|
    |**Instruction Register (IR)**|Holds current instruction being executed.|
    

---

## 🔵 2. Fundamental Steps in Instruction Execution

1. **Fetch Phase**:
    
    - `IR ← [ [PC] ]`
        
    - Fetch instruction from memory location pointed by PC and load it into IR.
        
2. **Increment PC**:
    
    - `PC ← [PC] + 4`
        
    - (Assuming 32-bit instructions, byte addressable memory, so next instruction is 4 bytes ahead.)
        
3. **Execute Phase**:
    
    - Decode and perform operation as per instruction in IR.
        

---

## 🔵 3. Processor Organization

- Main components:
    
    - **Datapath**: ALU, Registers, Bus.
        
    - **Control Unit**: Controls signals to datapath components.
        
- **Single-Bus Organization**:
    
    - One common bus connects all components.
        
    - Only **one transfer** at a time.
        

---

## 🔵 4. Executing an Instruction (General Actions)

Operations during execution:

1. **Transfer**: Move data between processor registers or ALU.
    
2. **ALU Operation**: Perform arithmetic or logic operation.
    
3. **Memory Read**: Fetch contents from memory to processor.
    
4. **Memory Write**: Store data from processor to memory.
    

---

## 🔵 5. Register Transfers and Clocking

- **Clock**: All transfers and operations happen **synchronously** with clock signals.
    
- Example:
    
    - Gating a register for **input** and **output** at clock edges.
        

---

## 🔵 6. Performing an ALU Operation

- **ALU**: A combinational circuit (no internal memory).
    
- Sequence to add contents of R1 and R2, store result in R3:
    
    1. `R1out`, `Yin` → Move R1 to temporary register Y.
        
    2. `R2out`, `SelectY`, `Add`, `Zin` → Add R2 and Y, store result in Z.
        
    3. `Zout`, `R3in` → Transfer Z into R3.
        

---

## 🔵 7. Fetching a Word from Memory

- **Steps**:
    
    1. `MAR ← [R1]` → Copy address from register R1 to Memory Address Register (MAR).
        
    2. **Start Read** operation.
        
    3. **Wait for MFC (Memory Function Completed)** signal.
        
    4. `MDR ← Memory contents`.
        
    5. `R2 ← [MDR]`.
        

|Signal/Operation|Meaning|
|:--|:--|
|**MAR**|Address to memory|
|**MDR**|Data from/to memory|
|**MFC**|Signal from memory that read/write completed|

---

## 🔵 8. Storing a Word into Memory

- **Steps**:
    
    1. `R1out`, `MARin`
        
    2. `R2out`, `MDRin`
        
    3. `Write`
        
    4. Wait for `WMFC` (Write MFC).
        

---

## 🔵 9. Execution of a Complete Instruction (Example)

Instruction: `Add (R3), R1`

- Step-by-step control sequence:
    

|Step|Action|
|:--|:--|
|1|Fetch instruction into IR.|
|2|Fetch operand from memory location pointed by R3 into MDR.|
|3|Perform addition (MDR + R1).|
|4|Store result back into R1.|

✅ **Uses single-bus for all communication inside CPU.**

---

## 🔵 10. Execution of Branch Instructions

- **Branch Instruction**:
    
    - Changes the value of PC.
        
    - PC ← PC + Offset
        
- **Steps** for Unconditional Branch:
    
    1. Fetch instruction.
        
    2. Decode and add offset to PC.
        
    3. Load new value into PC.
        
- **Conditional Branch**:
    
    - Branch occurs only if a **Condition Code** (N, Z, etc.) satisfies the condition.
        

---

## 🔵 11. Multiple-Bus Organization

- Improves performance by having **multiple buses**.
    
- **3-bus architecture**:
    
    - **Bus A**: Source 1
        
    - **Bus B**: Source 2
        
    - **Bus C**: Destination
        

✅ Multiple transfers can happen in one clock cycle!

**Example: `Add R4, R5, R6`** using 3-bus system.

---

## 🔵 12. Control Signal Generation

### 12.1 Hardwired Control

- Uses fixed logic circuits to generate control signals.
    
- **Fast but inflexible**.
    
- Suitable for simple CPUs.
    

Structure:

- **Decoder** + **Counter** → Generates correct sequence of control signals.
    

---

### 12.2 Microprogrammed Control

- Control signals generated using a **program** stored in **Control Store**.
    
- More flexible, slower.
    

|Term|Meaning|
|:--|:--|
|**Control Word (CW)**|A word where each bit controls one signal.|
|**Microroutine**|Sequence of CWs to implement one machine instruction.|
|**Microinstruction**|One control word.|
|**Control Store**|Memory storing all microroutines.|
|**Microprogram Counter (μPC)**|Reads next CW from control store.|

---

## 🔵 13. Example of Microinstructions

**Microprogram control sequence for `Add (R3), R1`:**

|Micro-step|Control Signals|
|:--|:--|
|1|`PCout`, `MARin`, `Read`, `Select4`, `Add`, `Zin`|
|2|`Zout`, `PCin`, `Yin`, `WMFC`|
|3|`MDRout`, `IRin`|
|4|`R3out`, `MARin`, `Read`|
|5|`MDRout`, `Yin`, `WMFC`|
|6|`R1out`, `SelectY`, `Add`, `Zin`|
|7|`Zout`, `R1in`, `End`|

---

## 🔵 14. Control Signal Optimization

- **Field Encoded Microinstructions**:
    
    - Groups mutually exclusive signals together.
        
    - Reduces microinstruction length.
        

|Field|Function|
|:--|:--|
|F1|Source select|
|F2|Destination select|
|F3|ALU operation|
|F4|Memory action (Read/Write)|
|F5|Clock control|

---

## 🔵 15. Microinstruction Organization

|Type|Characteristics|
|:--|:--|
|**Horizontal Microprogramming**|Minimal encoding, faster, wide control word.|
|**Vertical Microprogramming**|Highly encoded, slower, narrow control word.|

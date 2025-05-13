###  1. Data Conversions Overview

#### Types:

1. **Digital-to-Digital**
    
2. **Analog-to-Digital**
    
3. **Digital-to-Analog**
    

---

###  1.1 Digital-to-Digital Conversion

####  Techniques:

- **Line Coding**: Required for all digital signals.
    
- **Block Coding**: Optional, adds redundancy.
    
- **Scrambling**: Optional, for synchronization.
    

#### 📌 Line Coding:

- Converts binary data (1s & 0s) into digital signal.
    
- Example: `1 → +V`, `0 → -V`.
    

#### 🧮 Relation:

- **Data Rate (bps)**: Number of bits per second.
    
- **Signal Rate (Baud)**: Signal elements per second.
    
- **Formula:**  
    `S = c × N × (1/r)`  
    where:
    
    - `S`: Signal rate in bauds
        
    - `N`: Data rate in bps
        
    - `r`: Bits per signal element
        
    - `c`: Case factor (efficiency)
        

---

####  Line Coding Schemes:

1. **Unipolar NRZ**:
    
    - Single voltage (+V for 1, 0V for 0)
        
    - Simple, but has DC component.
        
2. **Polar NRZ**:
    
    - `NRZ-L`: Level based (+V for 1, -V for 0)
        
    - `NRZ-I`: Inversion on 1, no change on 0
        
3. **Polar RZ**:
    
    - Uses 3 levels (+V, 0, -V)
        
    - Mid-bit transition. High bandwidth use.
        
4. **Manchester**:
    
    - Mid-bit transition.
        
    - `1 = Low → High`, `0 = High → Low`
        
5. **Differential Manchester**:
    
    - Mid-bit transition always.
        
    - `0 = Transition at start`, `1 = No transition at start`
        
6. **Bipolar AMI & Pseudoternary**:
    
    - `AMI`: 0 = 0V, 1 = +V / -V alternately
        
    - `Pseudoternary`: 1 = 0V, 0 = +V / -V alternately
        
7. **Multilevel Schemes**:
    
    - Use combinations like 2B1Q (2 bits → 1 Quaternary signal)
        
    - Increase bit rate, reduce baud rate
        
8. **Multi-transition Coding**:
    
    - Adds forced transitions for better sync
        
    - Bandwidth-efficient (sometimes < bit rate)
        

---

####  Block Coding:

- Ensures accurate reception by adding redundancy.
    
- **Notation**: mB/nB (m-bit block replaced by n-bit block)
    
- Steps:
    
    1. Division
        
    2. Substitution
        
    3. Combination
        

---

####  Scrambling:

Used when long sequences of zeros cause sync loss.

1. **B8ZS (Bipolar with 8-Zero Substitution):**
    
    - Replaces `00000000` with `000VB0VB`
        
    - `V`: Violation (same polarity as previous)
        
    - `B`: Bipolar (opposite polarity)
        
2. **HDB3 (High-Density Bipolar 3-Zero):**
    
    - Replaces 4 consecutive 0s with `000V` or `B00V`
        
    - Based on parity of previous 1s
        

---

###  2. Analog-to-Digital Conversion

####  1. Pulse Code Modulation (PCM):

**Steps:**

1. **Sampling**:
    
    - Converts analog → discrete
        
    - Types: Ideal, Natural, Flat-top
        
    - Sampling interval = Ts; frequency = fs = 1/Ts
        
2. **Quantization**:
    
    - Converts samples → finite values
        
    - `d = (Vmax - Vmin) / L`
        
    - Introduces quantization error
        
3. **Encoding**:
    
    - Converts quantized values → binary code
        
    - `n bits = log₂L`
        

---

####  2. Delta Modulation (DM):

- Sends only the **difference** between samples.
    
- `1` = increase, `0` = decrease
    
- Easier than PCM, but less accurate.
    

**Components:**

- **Modulator**: Builds staircase signal
    
- **Demodulator**: Reconstructs using LPF (Low-Pass Filter)
    

---

###  3. Digital-to-Analog Conversion

####  Techniques:

1. **Amplitude Shift Keying (ASK):**
    
    - Data = binary
        
    - Carrier = analog
        
    - 1 → carrier ON, 0 → carrier OFF
        
    - 🟢: Simple, low bandwidth
        
    - 🔴: Noise sensitive
        
2. **Frequency Shift Keying (FSK):**
    
    - Binary 1 → high freq, 0 → low freq
        
    - 🟢: Less noise
        
    - 🔴: Higher bandwidth
        
3. **Phase Shift Keying (PSK):**
    
    - Phase changes based on bit value
        
    - Amplitude & freq remain constant
        

---

###  4. Configuring DTE-DCE Interface

- **DTE**: End-user device (PC, Router)
    
- **DCE**: Communication device (Modem, CSU/DSU)
    

####  Pin Configurations:

|Connector|DTE Tx|DTE Rx|DCE Tx|DCE Rx|
|---|---|---|---|---|
|25 pin|Pin 2|Pin 3|Pin 3|Pin 2|
|9 pin|Pin 3|Pin 2|Pin 2|Pin 3|

- DCE provides **clocking** to DTE.
    
- Crossover cables needed for DTE-DTE or DCE-DCE.
    

---

###  5. Shannon Capacity

#### 📌 Formula:

`C = B × log₂(1 + S/N)`

Where:

- `C`: Channel capacity (bps)
    
- `B`: Bandwidth (Hz)
    
- `S`: Signal power
    
- `N`: Noise power
    
- As **S/N (SNR)** or **B** increases → Capacity `C` increases
    
- Sets theoretical limit, not practical
    

##  6. Multiplexing – In-Depth Explanation

### 🔸 What is Multiplexing?

Multiplexing is a technique used to **combine multiple signals** and send them over a **single communication channel** or medium.  
This helps in efficient usage of bandwidth and reduces the cost of separate channels for each user.

Think of it like:

> 📦 Packing multiple small parcels (signals) into one big box (channel) to send them all together.

---

###  1. **FDM – Frequency Division Multiplexing**

#### 📌 Key Points:

- Used for **analog signals** (continuous signals like voice, TV broadcast).
    
- Each signal is assigned **a different frequency band** within the available bandwidth.
    
- All signals are sent **simultaneously**, but on different frequencies.
    

#### 🧠 Analogy: 

> Like tuning your radio — different stations (signals) play at different frequencies (bands) without interfering.

#### 📷 Example Applications:

- Cable TV (each channel has its own frequency)
    
- FM/AM Radio
    
- Old telephone systems
    

#### 🔄 De-Multiplexing:

- At the receiver, each frequency band is **filtered out** separately to extract the original signal.
    

---

###  2. **WDM – Wavelength Division Multiplexing**

#### 📌 Key Points:

- Very similar to FDM, **but for light signals** used in **fiber optics**.
    
- Different **light wavelengths (colors)** are used to carry multiple data streams on the same optical fiber.
    
- Uses devices like **prisms** to split and combine these light wavelengths.
    

#### 🧠 Analogy:

> Like passing multiple colored lights through a prism — each color (wavelength) carries a separate signal.

#### 📷 Example Applications:

- Optical fiber internet backbone
    
- Long-distance telecom systems
    
- Undersea fiber optic cables
    

---

###  3. **TDM – Time Division Multiplexing**

#### 📌 Key Points:

- Used for **digital signals** (discrete bits like 0s and 1s).
    
- The channel is divided into **equal time slots**.
    
- Each signal gets a **turn (slot)** to transmit its data in a round-robin fashion.
    

#### 📂 Two Types:

1. **Synchronous TDM**:
    
    - Every source gets a time slot **even if it has no data**.
        
    - Wastes bandwidth if sources are idle.
        
2. **Asynchronous (Statistical) TDM**:
    
    - Only **active sources** are given slots.
        
    - More efficient.
        

#### 🧠 Analogy:

> Like people taking turns to speak on a walkie-talkie – each one gets a specific time to talk.

#### 📷 Example Applications:

- Digital telephone networks
    
- DSL connections
    
- Computer buses
    

---

### 📝 Summary Table:

|Type|Signal Type|Multiplexing Medium|Used In|
|---|---|---|---|
|FDM|Analog|Frequency bands|Cable TV, Radio|
|WDM|Optical|Light wavelengths|Fiber optics|
|TDM|Digital|Time slots|Telecom, Internet|

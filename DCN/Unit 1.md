
## 🔹 1. Introduction to Computer Networks

A **computer network** is a collection of interconnected devices (nodes) that can communicate and share resources (files, printers, internet, etc.).

### 📌 **Need for Computer Networks**

- Resource sharing (hardware/software)
    
- Communication (email, chat, video calls)
    
- Data sharing and access control
    
- Centralized data management and backup


---

## 🔹 2. Types of Computer Networks

| Type                                | Description                                           | Example          |
| ----------------------------------- | ----------------------------------------------------- | ---------------- |
| **LAN** (Local Area Network)        | Small geographical area; high speed; privately owned  | Office, School   |
| **MAN** (Metropolitan Area Network) | Medium area (city); interconnects LANs                | Cable TV network |
| **WAN** (Wide Area Network)         | Large geographical area; uses leased lines/satellites | Internet         |
| **PAN** (Personal Area Network)     | Very small area; close-range wireless communication   | Bluetooth        |

### 📊 **Comparison Table**

|Feature|LAN|MAN|WAN|
|---|---|---|---|
|Area|Small|City|Global|
|Speed|High|Medium|Low|
|Ownership|Private|Govt/Private|Govt/ISP|
|Cost|Low|Medium|High|

---

## 🔹 3. Network Topologies

Topology = Physical or logical layout of network nodes and connections.

### 🔸 **Bus Topology**

- Single backbone cable; terminators at ends.
    
- Signal travels in both directions.
    
- **Pros**: Simple, inexpensive
    
- **Cons**: Difficult troubleshooting, limited devices
    

### 🔸 **Ring Topology**

- Each device connects to two others in a circular path.
    
- **Unidirectional** or **Bidirectional**.
    
- **Pros**: Equal access, orderly communication
    
- **Cons**: Failure in one device affects entire network
    

### 🔸 **Star Topology**

- Devices connect to a **central hub/switch**.
    
- **Pros**: Easy to install/manage
    
- **Cons**: Central point of failure
    

### 🔸 **Mesh Topology**

- Every node connected to every other node.
    
- **Pros**: High redundancy, no traffic issues
    
- **Cons**: Expensive, complex cabling
    

### 🔸 **Tree Topology**

- Hierarchical combination of star and bus.
    
- **Pros**: Scalable, fault isolation
    
- **Cons**: Root failure can disable entire tree
    

### 🔸 **Hybrid Topology**

- Combination of two or more topologies.
    
- **Pros**: Flexible and robust
    
- **Cons**: Costly and difficult to design
    

📌 **Formula for Mesh connections:**

No. of Links=n(n−1)2\text{No. of Links} = \frac{n(n-1)}{2}

---

## 🔹 4. Network Devices

| Device       | Layer     | Function                              |
| ------------ | --------- | ------------------------------------- |
| **Hub**      | Physical  | Broadcasts data to all ports          |
| **Switch**   | Data Link | Forwards data to specific MAC address |
| **Router**   | Network   | Routes packets using IP addresses     |
| **Bridge**   | Data Link | Connects two similar networks         |
| **Repeater** | Physical  | Regenerates signals                   |
| **Modem**    | Physical  | Converts digital ↔ analog             |

---

## 🔹 5. OSI Reference Model (7 Layers)

A theoretical model for understanding network communication.

| Layer               | Function                    | Example      |
| ------------------- | --------------------------- | ------------ |
| **7. Application**  | User interface (web, email) | HTTP, FTP    |
| **6. Presentation** | Encoding, encryption        | JPEG, SSL    |
| **5. Session**      | Manages sessions            | API sessions |
| **4. Transport**    | End-to-end delivery         | TCP, UDP     |
| **3. Network**      | Routing, IP addressing      | IP, ICMP     |
| **2. Data Link**    | MAC address, framing        | Ethernet     |
| **1. Physical**     | Transmit raw bits           | Cables       |

---

## 🔹 6. TCP/IP Model (4 Layers)

Real-world model used on the internet.

|TCP/IP Layer|Corresponding OSI Layers|
|---|---|
|Application|Application, Presentation, Session|
|Transport|Transport|
|Internet|Network|
|Network Access|Data Link + Physical|

---

## 🔹 7. Transmission Media

### 📦 **Guided Media (Wired)**

|Type|Features|
|---|---|
|**Twisted Pair**|Inexpensive, short distances|
|**Coaxial Cable**|Better shielding, used in TV systems|
|**Fiber Optic**|Very high speed, long distances|

### 📡 **Unguided Media (Wireless)**

|Type|Frequency|Range|Usage|
|---|---|---|---|
|**Radio Waves**|Low|Long|FM Radio|
|**Microwaves**|High|Medium|Cell phones|
|**Infrared**|Very High|Short|Remote controls|

---

## 🔹 8. Analog and Digital Signals

|Type|Description|
|---|---|
|**Analog**|Continuous wave (e.g., sine wave)|
|**Digital**|Discrete wave (0s and 1s)|

📌 **Signal Parameters:**

- **Amplitude** – Height of wave
    
- **Frequency** – How fast it cycles
    
- **Phase** – Shift in time
    

---

## 🔹 9. Time and Frequency Domain

- **Time Domain**: Signal vs. Time
    
- **Frequency Domain**: Signal's frequency components
    
- Used for **bandwidth analysis**, filtering
    

---

## 📝 Sample Exam Questions

### 🔸 Q1. Explain the OSI Model with layers and functions.

**Ans:** Write all 7 layers with function + examples (use table).

### 🔸 Q2. Compare LAN, MAN, and WAN.

**Ans:** Write a comparison table with area, speed, cost, etc.

### 🔸 Q3. Describe any 3 types of network topologies.

**Ans:** Explain with diagrams + pros/cons.

---

## 📌 Diagrams to Practice

- OSI Model 7-Layer Diagram
    
- Network Topologies (Star, Bus, Ring)
    
- Guided vs Unguided Media (with cable types)
    
- Signal waveform examples
    

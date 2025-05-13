
# 📘 UNIT 4 – **Network Layer (Layer 3 of OSI Model)**

_(Complete with diagrams, examples, key definitions & expected questions)_

---

## 🔹 1. Introduction to Network Layer

The **Network Layer** is the **3rd layer** in the OSI model.  
It is responsible for **delivering packets from source to destination** across **multiple networks (internetworking)**.

### 🔸 Responsibilities:

- Logical Addressing (IP)
    
- Routing
    
- Packet Forwarding
    
- Fragmentation & Reassembly
    
- Error Handling & Congestion Control (basic)
    

---

## 🔹 2. Logical Addressing (IP Addressing)

The **network layer** uses **logical addresses** (like IP) to identify each device uniquely across internetworks.

### 📌 IPv4 Address:

- 32-bit address, divided into **4 octets (dotted decimal)**  
    Example: `192.168.1.1`
    
- Divided into **Network ID** and **Host ID**
    

---

## 🔹 3. Packet Switching

Network layer uses **packet switching** for efficient delivery.

|Type|Description|
|---|---|
|**Datagram**|Packets are routed independently (like postal system). E.g., Internet (IP)|
|**Virtual Circuit**|All packets follow same path. Setup before transmission. E.g., ATM|

---

## 🔹 4. Routing Concepts

### ✨ Routing:

Selecting the **best path** to reach a destination.

### 🔸 Types of Routing:

|Type|Description|
|---|---|
|**Static Routing**|Manual, fixed paths|
|**Dynamic Routing**|Routers calculate routes using protocols|
|**Default Routing**|All unknown packets sent to a specific router|

---

## 🔹 5. Routing Algorithms

### 🔸 Classification

|Category|Algorithms|
|---|---|
|**Non-Adaptive**|Shortest Path, Flooding|
|**Adaptive**|Distance Vector, Link State|

---

### 🔸 5.1 Shortest Path Routing

- Uses algorithms like **Dijkstra’s Algorithm**.
    
- Routes based on **least cost** (e.g., hops, time, distance).
    

📌 _Dijkstra’s Algorithm_:

- Graph-based
    
- Builds shortest tree from source
    
- Greedy approach
    

---

### 🔸 5.2 Flooding

- Every incoming packet is sent out on **all outgoing links** (except incoming one).
    
- **Simple but inefficient** (causes network congestion).
    

---

### 🔸 5.3 Distance Vector Routing

- Routers maintain a table (vector) of distances to all destinations.
    
- Uses **Bellman-Ford algorithm**.
    
- Exchange routing tables with neighbors periodically.
    

📌 Problems:

- **Count-to-infinity** problem
    
- Solved by: **Split Horizon**, **Poison Reverse**
    

---

### 🔸 5.4 Link State Routing

- Routers **flood** the network with info about their links.
    
- Each router builds the entire **network topology** and computes shortest path (Dijkstra).
    
- More complex, but converges faster than Distance Vector.
    

|Feature|Distance Vector|Link State|
|---|---|---|
|Routing Table|From neighbors|From full topology|
|Convergence Time|Slower|Faster|
|Algorithm|Bellman-Ford|Dijkstra|
|Bandwidth Usage|Less|More|

---

## 🔹 6. IP Protocol and Datagram

### ✨ IP: Internet Protocol (v4/v6)

- **Connectionless**, **unreliable** delivery of datagrams.
    
- Adds **logical addressing**, **fragmentation**, and **routing**.
    

### 📦 IP Datagram Format:

|Field|Description|
|---|---|
|Version|4 bits (IPv4 = 4)|
|Header Length|Length of IP header|
|Total Length|Total packet length|
|ID/Flags/Offset|Fragmentation control|
|TTL|Time To Live (hop limit)|
|Protocol|Upper layer (e.g., TCP=6, UDP=17)|
|Source IP|Sender’s IP address|
|Destination IP|Receiver’s IP address|
|Checksum|Header error detection|

---

## 🔹 7. Fragmentation and Reassembly

Occurs when a packet is too large for the next network’s MTU (Maximum Transmission Unit).

- **Fragmentation**: Split into smaller packets (done at sender/router)
    
- **Reassembly**: Combine at destination
    

📌 Fields involved:

- Identification
    
- Fragment Offset
    
- More Fragments Flag
    

---

## 🔹 8. Congestion Control

Occurs when too many packets are in transit, causing delay or packet drop.

### 🔸 Techniques:

- **Packet dropping**
    
- **Choke packets**
    
- **Load shedding**
    
- **Traffic shaping**
    

📌 Congestion is handled at **Network Layer** (basic) and more in **Transport Layer** (TCP flow control).

---

## 🔹 9. ICMP – Internet Control Message Protocol

- Used by **network devices** to send error or control messages.
    
- Commonly used by **ping** or **traceroute**.
    

|Message Type|Use|
|---|---|
|Echo Request/Reply|Ping test|
|Destination Unreachable|No route or blocked|
|Time Exceeded|TTL expired|
|Redirect|Use better route|

---

## 📝 Expected Exam Questions

### Q1. Explain types of routing algorithms.

**Ans:** Use table format – Dijkstra, Distance Vector, Link State, Flooding.

### Q2. Write short notes on fragmentation and reassembly.

**Ans:** Define, explain IP fields involved, add diagram.

### Q3. Compare Distance Vector and Link State Routing.

**Ans:** Use comparison table, mention pros and cons.

### Q4. Explain IP Datagram format.

**Ans:** Draw header, explain each field briefly.

---

## 🧠 Quick Recap Table

|Topic|Key Points|
|---|---|
|Logical Addressing|IP addresses|
|Routing|Path selection, algorithms|
|Packet Switching|Datagram vs Virtual Circuit|
|Fragmentation|IP packet splitting|
|Congestion Control|Prevent overload, TTL, shaping|
|Protocols|IP, ICMP|

---

Would you like a **PDF version with diagrams**, or should I continue with **Unit 5 detailed notes** next?
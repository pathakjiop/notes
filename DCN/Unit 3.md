
# 📘 UNIT 3 – **Data Link Layer (DLL)**

_(In-depth concepts, examples, diagrams & exam questions)_

---

## 🔹 1. Introduction to DLL

The **Data Link Layer** is the **2nd layer** in the OSI Model.  
It is responsible for **node-to-node** communication and ensures **error-free** and **reliable** transmission over the physical layer.

### ✨ Responsibilities:

- Framing
    
- Physical addressing
    
- Flow control
    
- Error detection and correction
    
- Access control
    

---

## 🔹 2. Framing

Framing is the process of dividing a stream of bits into **manageable data units** called **frames**.

### 📘 Framing Techniques:

|Method|Description|
|---|---|
|**Length Count**|Frame starts with a field that indicates frame length|
|**Byte Stuffing**|Uses special characters (e.g., FLAG, ESC) to mark frame boundaries|
|**Bit Stuffing**|Inserts 0 after 5 consecutive 1s to prevent flag imitation|

📌 _Frame Delimiters Example (Bit Stuffing):_  
Data: `01111110` (flag pattern)  
Actual Data: `01111101110` → Stuffed as `011111010110`

---

## 🔹 3. Physical Addressing

- DLL adds **MAC addresses** of source and destination in the **frame header**.
    
- Used in LAN environments (e.g., Ethernet uses MAC 48-bit addresses).
    

---

## 🔹 4. Flow Control

Ensures that the **sender does not overwhelm** the receiver with data.

### 🔸 Techniques:

|Method|Description|
|---|---|
|**Stop-and-Wait**|Sender waits for ACK before sending next frame|
|**Sliding Window**|Sender can send multiple frames before receiving ACK|

#### 📘 Sliding Window:

- Uses sequence numbers and acknowledgments.
    
- **Window size** controls number of frames that can be sent without ACK.
    

---

## 🔹 5. Error Control

### 🔸 Error Detection Techniques:

|Method|How it works|
|---|---|
|**Parity Bit**|Adds 1 bit to make number of 1s even/odd|
|**Checksum**|Sum of all segments, sent with data|
|**CRC** (Cyclic Redundancy Check)|Uses polynomial division (generator) to detect errors|

📌 _CRC = Most powerful error detection method_

### 🔸 Error Correction Technique:

|Method|Description|
|---|---|
|**Hamming Code**|Adds redundancy bits to correct 1-bit errors|
|**ARQ** (Automatic Repeat reQuest)|Resends frame when error is detected|

#### 🌀 Types of ARQ:

1. **Stop-and-Wait ARQ**
    
2. **Go-Back-N ARQ**
    
3. **Selective Repeat ARQ**
    

---

## 🔹 6. Access Control

Used when **multiple devices** share the same medium.

### 🔸 Techniques:

|Method|Description|Example|
|---|---|---|
|**Random Access**|Any device can transmit randomly|ALOHA, CSMA|
|**Controlled Access**|Access is given in a controlled way|Polling, Token Passing|
|**Channelization**|Divide channel among users|FDMA, TDMA, CDMA|

---

## 🔹 7. Random Access Protocols

### 🔸 ALOHA (Pure & Slotted)

|Protocol|Working|
|---|---|
|**Pure ALOHA**|Send any time, if collision → wait random time and resend|
|**Slotted ALOHA**|Time is divided into slots; send at start of slot|

📌 **Efficiency**:

- Pure ALOHA ≈ 18.4%
    
- Slotted ALOHA ≈ 36.8%
    

### 🔸 CSMA (Carrier Sense Multiple Access)

|Type|Description|
|---|---|
|**CSMA**|Listen to channel before transmitting|
|**CSMA/CD**|Collision Detection (Ethernet)|
|**CSMA/CA**|Collision Avoidance (Wi-Fi)|

---

## 🔹 8. Controlled Access Protocols

### 🔸 Polling:

- Central controller polls each device in turn.
    
- **Master–slave** configuration.
    

### 🔸 Token Passing:

- A **token** (small message) is passed among devices.
    
- Only the token holder can transmit.
    

📌 Used in **Token Ring LAN**.

---

## 🔹 9. Channelization Protocols

### 🔸 FDMA (Frequency Division Multiple Access):

- Channel divided into frequency bands.
    
- Used in analog systems.
    

### 🔸 TDMA (Time Division Multiple Access):

- Each station gets time slot.
    
- Used in digital communication.
    

### 🔸 CDMA (Code Division Multiple Access):

- Uses unique code for each user.
    
- All users can send simultaneously.
    

---

## 🔹 10. Example: Frame Format in DLL (e.g., HDLC)

|Field|Function|
|---|---|
|Flag|Frame boundary (01111110)|
|Address|Receiver address|
|Control|Frame type, ACK, sequence|
|Data|Actual message|
|FCS|Error check (CRC)|
|Flag|End of frame|

---

## 📝 Sample Exam Questions

### Q1. Explain Framing with Byte Stuffing and Bit Stuffing.

**Ans:** Definitions, use examples with FLAG/ESC characters and stuffed data.

### Q2. Compare Stop-and-Wait and Sliding Window Protocol.

**Ans:** Table format comparison of efficiency, utilization, delay.

### Q3. Describe Go-Back-N and Selective Repeat ARQ.

**Ans:** Use diagrams and sequence numbers.

### Q4. Write short notes on:

- CSMA/CD
    
- Token Passing
    
- Hamming Code
    

---

## 🧠 Quick Revision Table

|Topic|Technique / Protocol|
|---|---|
|Error Detection|CRC, Parity, Checksum|
|Error Correction|Hamming, ARQ|
|Framing|Byte Stuffing, Bit Stuffing|
|Flow Control|Stop-and-Wait, Sliding Window|
|Access Control|CSMA, Polling, Token|
|Channelization|FDMA, TDMA, CDMA|

---

Would you like a **PDF version with diagrams and illustrations** for easy revision? Or shall I continue with **Unit 4 detailed notes** next?
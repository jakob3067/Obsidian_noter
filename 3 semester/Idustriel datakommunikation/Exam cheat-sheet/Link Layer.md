# **THE LINK LAYER — CHEAT SHEET**

## **1. Link Layer Services**

The link layer operates between adjacent nodes on the same link.

### **Flow Control**

- Prevents sender from overwhelming receiver.
- Ensures receiver buffers don’t overflow.

### **Error Detection / Correction**

- Detects (and sometimes corrects) bit errors caused by noise.
    
- Common methods:
    
    - **Parity bits** (single-bit error detection)
    - **Checksums**
    - **CRC (Cyclic Redundancy Check)** — strongest, used in Ethernet.
        

### **Duplex**

- **Half‑duplex:** nodes take turns transmitting.
- **Full‑duplex:** simultaneous send/receive (modern Ethernet).

## **2. IP Framing**

- Link layer encapsulates network-layer datagrams into **frames**.
    
- Frame includes:
    
    - **Header** (MAC addresses, type field)
    - **Payload** (IP datagram)
    - **Trailer** (CRC)
        
- Frame boundaries are meaningful only on the local link.
    

## **3. Error Detection Methods**

### **Parity**

- **Single-bit parity:** detects odd number of bit errors.
    
- **Two-dimensional parity:** can detect and correct some errors.
    

### **CRC (Cyclic Redundancy Check)**

- Sender divides data by a generator polynomial.
- Receiver checks remainder.
- Very strong detection; used in Ethernet, WiFi.
    

## **4. Multiple Access Problem**

When multiple nodes share a broadcast medium, they may transmit simultaneously → **collisions**.

Goal: coordinate access so only one transmits at a time.

## **5. Multiple Access Protocols**

### **TDMA (Time Division Multiple Access)**

- Time is divided into slots.
- Each node gets a slot.
- No collisions, but inefficient if nodes are idle.
    
### **FDMA (Frequency Division Multiple Access)**

- Frequency band divided into channels.
- Each node gets a frequency.
- Also avoids collisions; fixed allocation.

### **CSMA/CD (Carrier Sense Multiple Access with Collision Detection)**

- Used in classic Ethernet (not modern switched Ethernet).
- **Carrier sense:** listen before transmitting.
- **Collision detection:** stop transmitting if collision detected.
- **Binary exponential backoff:** after collision, wait random time; window doubles after each collision.
    

## **6. Binary Exponential Backoff**

- After 1st collision → choose random K from {0,1}.
- After 2nd → K from {0,1,2,3}.
- After m-th → K from {0…2^m − 1}.
- Wait **K × slot time** before retrying.
- Reduces repeated collisions under load.
    

## **7. Modern Ethernet (Switched Ethernet)**

- No longer uses CSMA/CD.
    
- Each host connects to a **switch**, not a shared bus.
    
- Switch characteristics:
    
    - Full‑duplex links
        
    - No collisions
        
    - Stores and forwards frames
        
    - Maintains MAC address table (self-learning)
        
- Provides **isolation** and **high throughput**.
    

## **8. MAC Address vs IP Address**

### **MAC Address**

- 48-bit hardware address (e.g., 00:1A:2B:3C:4D:5E).
    
- Flat, not hierarchical.
    
- Burned into NIC (but can be changed).
    
- Used for **local delivery** on a link.
    

### **IP Address**

- Network-layer address.
    
- Hierarchical (network + host).
    
- Used for **end-to-end** delivery across networks.
    

**Analogy:** MAC = street address inside a building IP = postal address across cities

## **9. ARP (Address Resolution Protocol)**

Maps **IP address → MAC address** on a local network.

### **How ARP Works**

1. Host broadcasts **ARP request**: “Who has IP X?”
    
2. Host with that IP replies with its MAC address.
    
3. Sender caches the mapping in **ARP table**.
    

### **Properties**

- Works only within a LAN.
    
- Stateless, dynamic, no authentication.
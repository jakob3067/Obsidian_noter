# **TRANSPORT LAYER — ONE‑PAGE CHEAT SHEET (Kurose & Ross)**

## **1. Transport Services**

Transport protocols provide services to applications running on end systems.

### **Reliability**

- Ensures **no data loss**, **no corruption**, **in‑order delivery**.
- Provided by **TCP**, not by UDP.

### **Throughput**

- Some applications need minimum throughput (e.g., video streaming).
- TCP throughput varies with congestion; UDP does not guarantee throughput.

### **Timing**

- Some apps need low delay (VoIP, gaming).
- UDP is preferred when timing > reliability.
    

### **Security**

- Provided via **TLS** on top of TCP (not by TCP itself).
    

## **2. Multiplexing & Demultiplexing**

- **Multiplexing:** Gathering data from multiple sockets and adding transport headers.
- **Demultiplexing:** Delivering received segments to the correct socket.
    
- Uses:
    - **Source/destination port numbers**
    - **IP addresses**
- UDP uses **(dest IP, dest port)**.
    
- TCP uses **(src IP, src port, dest IP, dest port)** → supports multiple connections to same server port.
    

## **3. UDP Packet vs TCP Segment**

### **UDP Packet (Datagram)**

- Header fields:
    
    - Source port
    - Destination port
    - Length
    - Checksum
        
- No reliability, ordering, or congestion control.
    

### **TCP Segment**

- Header fields include:
    
    - Source/destination ports
    - Sequence number
    - Acknowledgment number
    - Flags (SYN, ACK, FIN, RST)
    - Window size
    - Checksum
        
- Provides reliability, flow control, congestion control.
    

## **4. Connectionless vs Connection‑Oriented**

### **UDP — Connectionless**

- No handshake.
- Stateless.
- Unreliable, unordered.
- Low overhead, low delay.

### **TCP — Connection‑Oriented**

- Requires **3‑way handshake**.
    
- Maintains connection state.
    
- Reliable, ordered byte stream.
    

## **5. UDP**

- Minimal overhead.
    
- No congestion control → can send at application rate.
    
- Used for DNS, VoIP, gaming, streaming.
    
- Checksum detects corruption (optional in IPv4).
    

# **6. TCP**

## **TCP Handshaking (3‑Way)**

1. **SYN**
2. **SYN‑ACK**
3. **ACK** Connection established.

## **ACKs & Sequence Numbers**

- TCP uses **byte‑based** sequence numbers.
- ACKs are **cumulative** (ACK n = all bytes < n received).
- Duplicate ACKs indicate possible loss.

## **RTT Estimation**

- TCP estimates RTT using **Exponential Weighted Moving Average (EWMA)**:
    
    - EstimatedRTT = (1 − α)·EstimatedRTT + α·SampleRTT
        
- Timeout = EstimatedRTT + 4·DevRTT
    

## **Retransmission Mechanisms**

- **Timeout‑based** retransmission
- **Fast retransmit**: triggered by **3 duplicate ACKs**
    

# **7. Flow Control vs Congestion Control**

## **Flow Control**

- Prevents **receiver** from being overwhelmed.
    
	- Uses **receiver window (rwnd)**.
    
- Sender ensures:
    

SendWindow≤rwnd

## **Congestion Control**

- Prevents **network** from being overwhelmed.
    
- Uses **congestion window (cwnd)**.
    
- Sender ensures:
    

SendWindow=min⁡(rwnd,cwnd)

# **8. TCP Congestion Control Phases**

## **1. Slow Start**

- cwnd starts at **1 MSS**.
    
- Grows **exponentially**: cwnd = cwnd × 2 per RTT.
    
- Continues until **threshold (ssthresh)** reached or loss detected.
    

## **2. Congestion Avoidance**

- cwnd grows **linearly**: cwnd = cwnd + 1 MSS per RTT.
    
- Used after slow start or after recovery.
    

## **3. Fast Recovery**

- Triggered by **3 duplicate ACKs** (not timeout).
    
- ssthresh = cwnd / 2
    
- cwnd = ssthresh
    
- Then linear growth (avoidance).
    

Timeout → return to **slow start**.
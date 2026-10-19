# 🌐 **THE NETWORK LAYER — COMPLETE CHEAT SHEET**

# **1. DATA PLANE**

## **Data Plane vs Control Plane**

- **Data Plane:**
    
    - Operates _per packet_.
        
    - Responsible for **forwarding** packets from input → output.
        
    - Implemented in routers’ hardware/fast path.
        
- **Control Plane:**
    
    - Operates _per network-wide logic_.
        
    - Responsible for **routing** decisions (building forwarding tables).
        
    - Implemented via routing algorithms or SDN controllers.
        

## **Forwarding vs Routing**

- **Forwarding:**
    
    - Local action: move packet to correct output port.
        
    - Uses forwarding table.
        
- **Routing:**
    
    - Global process: compute paths through the network.
        
    - Uses algorithms (Dijkstra, Bellman-Ford).
        

## **Router Components**

1. **Input ports**
    
    - Line termination
        
    - Lookup, forwarding
        
    - Queuing
        
2. **Switching fabric**
    
    - Moves packets internally
        
3. **Output ports**
    
    - Queuing
        
    - Scheduling
        
4. **Routing processor**
    
    - Runs routing protocols (OSPF, BGP)
        

## **Switching Fabrics**

1. **Memory-based**
    
    - Packets copied via CPU/memory
        
    - Slowest
        
2. **Bus-based**
    
    - Shared bus
        
    - Only one packet at a time
        
3. **Crossbar**
    
    - Parallel connections
        
    - High throughput
        

## **Input/Output Queuing**

- Occurs when arrival rate > switching capacity.
    
- Can cause **packet loss**.
    

### **Head-of-Line (HOL) Blocking**

- In input queues, first packet blocks others behind it even if they could be forwarded.
    
- Limits throughput to ~58% in some cases.
    

## **Packet Scheduling**

- Determines which packet leaves next.
    

### **FIFO (First-In First-Out)**

- Simple, fair, but no prioritization.
    

### **Priority Queuing**

- Higher priority packets always served first.
    
- Risk: starvation of low-priority traffic.
    

### **Round Robin / Weighted Round Robin**

- Cycles through queues.
    
- Weighted version gives more bandwidth to selected queues.
    

## **IP Addressing**

### **IPv4 Structure**

- 32-bit address
- Written as dotted decimal (e.g., 192.168.1.1)

### **Subnetting**

- Splits network into smaller networks.
- Uses subnet mask (e.g., /24).
    

### **CIDR (Classless Inter-Domain Routing)**

- Format: `a.b.c.d/x`
- Allows variable-length prefixes.
- Enables **route aggregation**.

## **Forwarding Methods**

### **Destination-Based Forwarding**

- Uses destination IP only.

### **Longest Prefix Match**

- Router chooses entry with longest matching prefix.
- Implemented using tries or TCAM.

### **SDN/OpenFlow Forwarding**

- Rules can match on many fields:
    
    - IP, MAC, ports, protocol, etc.
        
- Controller installs flow rules.
    

## **IP Address Assignment**

### **Manual**

- Static configuration.
    

### **DHCP (Dynamic Host Configuration Protocol)**

- Automatically assigns IP, subnet mask, gateway, DNS.
    

## **DHCP Process (DORA)**

1. **Discover** (client → broadcast)
    
2. **Offer** (server → client)
    
3. **Request** (client → server)
    
4. **ACK** (server → client)
    

## **NAT (Network Address Translation)**

- Maps private IPs to a public IP.
    
- Uses NAT table with port mappings.
    
- Enables IPv4 address conservation.
    
- Breaks end-to-end principle.
    

## **IPv4 vs IPv6**

### **IPv4 Datagram**

- Variable-length header
    
- Fragmentation allowed
    
- 32-bit addresses
    

### **IPv6 Datagram**

- Fixed 40-byte header
    
- No fragmentation by routers
    
- 128-bit addresses
    
- Extension headers
    

### **Tunneling**

- IPv6 packet encapsulated inside IPv4 packet to traverse IPv4 networks.
    

# **2. CONTROL PLANE**

## **Routing Algorithms**

### **Goal**

- Find least-cost paths between nodes.
    

### **Graph Model**

- Routers = nodes
    
- Links = edges with weights (delay, cost, bandwidth)
    

## **Link-State vs Distance-Vector**

### **Link-State (LS)**

- Each router knows full topology.
    
- Runs **Dijkstra’s algorithm**.
    
- Used by OSPF.
    

### **Distance-Vector (DV)**

- Routers exchange distance vectors with neighbors.
    
- Uses **Bellman-Ford equation**:
    

dx(y)=min⁡v{c(x,v)+dv(y)}

### **Count-to-Infinity Problem**

- DV can take a long time to converge after failures.
    
- Caused by incorrect routing loops.
    

## **Autonomous Systems (AS)**

- Large networks under single administrative control.

### **Intra-AS Routing**

- Inside an AS
- Uses OSPF, IS-IS
- Goal: performance, consistency

### **Inter-AS Routing**

- Between ASes
- Uses **BGP**
- Goal: policy, economics, reachability

## **BGP (Border Gateway Protocol)**

### **Key Attributes**

- **AS-PATH:** list of ASes a route has traversed
    
- **NEXT-HOP:** next router to reach destination
    
- **LOCAL-PREF:** preference for outbound traffic
    

### **Hot Potato Routing**

- Send traffic to nearest exit point to minimize internal cost.
    

## **SDN vs Traditional Routing**

### **Traditional**

- Distributed control plane
- Routers run routing protocols
- Each router computes its own forwarding table

### **SDN**

- Centralized controller
- Global network view
- Switches follow controller-installed rules (OpenFlow)

## **Traceroute**

- Uses increasing TTL values.
- Each router returns ICMP “Time Exceeded”.
- Reveals path taken by packets.
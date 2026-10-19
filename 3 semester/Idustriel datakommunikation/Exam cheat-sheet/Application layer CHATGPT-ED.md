
## what is the application layer



# 🌐 The Application Layer — Study Guide

## 🧩 Network Applications

Network applications are programs that run on end systems and communicate over the network. Examples include:

- Web browsers & servers (HTTP)
- Email clients (SMTP, IMAP)
- Video streaming apps
- Online games

**Key idea:** Applications run on hosts — _not_ inside the network core. The network provides services; applications use them.

## 🏛️ Application Architectures

Two major models:

### **1. Client–Server Architecture**

- **Client** initiates communication (e.g., browser)
- **Server** waits for requests (e.g., web server)
- Server is always-on, has a fixed IP
- Clients may be intermittently connected

### **2. Peer-to-Peer (P2P)**

- No always-on server
- Peers act as both clients and servers
- Highly scalable (e.g., BitTorrent)

## 🔢 IP Addresses & Ports

### **IP Address**

Identifies a host on the network (e.g., `192.168.1.10`).

### **Port Number**

Identifies a specific process/application on that host.

Examples:

- HTTP → port **80**
- HTTPS → port **443**
- DNS → port **53**

Together they form a **socket address**: `IP:Port` (e.g., `142.250.187.78:80`)

## 🔌 Socket Programming

A **socket** is the interface between an application and the transport layer.

Two main types:

- **TCP sockets** → reliable, connection-oriented
- **UDP sockets** → fast, connectionless, no reliability

Applications use sockets to:

- Send data
- Receive data
- Establish connections (TCP)

## 🚚 Transport Layer Services Used by Applications

Applications choose transport services based on needs:

| Service Need        | TCP       | UDP |
| ------------------- | --------- | --- |
| Reliability         | ✔         | ✖   |
| Ordered delivery    | ✔         | ✖   |
| Congestion control  | ✔         | ✖   |
| Low latency         | ✖         | ✔   |
| Streaming/real-time | Sometimes | ✔   |

Examples:

- HTTP → TCP
- DNS → UDP (mostly)
- Video streaming → often UDP

# 🌍 HTTP — HyperText Transfer Protocol

## 📄 Webpage Structure

A webpage is usually composed of:

- HTML file
- Images
- CSS
- JavaScript
- Other embedded objects

Each object often requires its own HTTP request.

## 🔁 Persistent vs Non-Persistent Connections

### **Non-Persistent HTTP (HTTP/1.0)**

- One TCP connection per object
- Slow due to repeated handshakes

### **Persistent HTTP (HTTP/1.1+)**

- One TCP connection for multiple objects
- Faster, less overhead
- Supports pipelining

## 🍪 Cookies & State

HTTP is **stateless**, so cookies allow servers to remember users.

Cookies include:

- Cookie header in HTTP messages
- Stored in browser
- Used for login sessions, shopping carts, personalization

## 📦 Web Caching (Proxy Servers)

A **web cache** stores copies of recently accessed webpages.

Benefits:

- Reduces response time
- Reduces traffic to origin servers
- Improves scalability

Caches use **conditional GET** to check freshness.

# 🔎 DNS — Domain Name System

## 🧱 DNS Structure

DNS is a **distributed, hierarchical** database.

### Levels:

1. **Root servers**
2. **Top-Level Domain (TLD) servers** (.com, .org, .dk, etc.)
3. **Authoritative servers** (store actual domain records)
4. **Local DNS resolvers** (your ISP or campus)

## 📚 DNS Resource Records (RRs)

Each DNS entry is a **resource record**:

Format: `(Name, Value, Type, TTL)`

Examples:

- **A record** → hostname → IPv4 address
- **AAAA record** → hostname → IPv6 address
- **NS record** → domain → authoritative server
- **CNAME** → alias → canonical name
- **MX** → mail server

## 🧠 DNS Caching

DNS resolvers cache responses to speed up future lookups.

- Reduces load on root/TLD servers
- Improves performance
- Entries expire based on TTL

## ⚠️ Centralized DNS Issues

A single centralized DNS server would suffer from:

- Huge traffic load
- Single point of failure
- Long delays for distant clients
- No scalability

This is why DNS is **distributed and hierarchical**.

## 🌲 Hierarchical DNS

The hierarchy solves the problems above by:

- Distributing load
- Providing redundancy
- Allowing caching at every level
- Scaling globally
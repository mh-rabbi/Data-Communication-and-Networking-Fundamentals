

# 📘 Networking Concepts Recap  
*Based on CSC 465 Lectures

---

## 📁 Lecture 1: Communications and Networks

### 🔹 Key Concepts:
- **Computer Communications**: Transfer of data, instructions, and information between devices.
- **Connectivity & Wireless Revolution**: Linking people/resources via mobile/wireless tech.
- **Communication System Elements**:
  - Sending/receiving devices
  - Communication channel
  - Connection devices (e.g., modems)
  - Data transmission specs

### 🔹 Communication Channels:
- **Physical**: Twisted-pair, coaxial, fiber-optic cables
- **Wireless**: Infrared, RF (Wi-Fi, Bluetooth), microwave, satellite

### 🔹 Data Transmission:
- **Bandwidth**: Voiceband, medium band, broadband, baseband
- **Data Flow**: Serial vs. parallel
- **Data Direction**: Simplex, half-duplex, full-duplex
- **Protocols**: Rules for data exchange (e.g., TCP/IP, HTTP, FTP)

### 🔹 Networks:
- **Types**: LAN, WLAN, PAN, MAN, WAN
- **Architecture**: Topologies (bus, ring, star, tree, mesh), Strategies (terminal, client/server, P2P, distributed)
- **Organizational Networks**: Intranet, extranet, firewalls, VPNs

---

## 📁 Lecture 2: Network Models

### 🔹 Layered Models:
- **OSI Model** (7 layers):
  - Application, Presentation, Session, Transport, Network, Data Link, Physical
- **TCP/IP Model** (4/5 layers):
  - Application, Transport, Internet, Link, Physical (optional)

### 🔹 Key Functions:
- **Application**: User services (HTTP, FTP, SMTP)
- **Transport**: End-to-end communication (TCP, UDP)
- **Network**: Routing (IP)
- **Data Link**: Framing, error control
- **Physical**: Bit transmission

### 🔹 Addressing:
- **Physical**: MAC address (e.g., `07:01:02:01:2C:4B`)
- **Logical**: IP address
- **Port**: Process identification (e.g., port 80 for HTTP)
- **Specific**: Email, URL addresses

---

## 📁 Lecture 3: Application Layer (1)

### 🔹 Domain Name System (DNS):
- Maps domain names to IP addresses
- **Hierarchical Name Space**: Root, TLDs (generic, country), subdomains
- **FQDN vs. PQDN**: Fully Qualified vs. Partially Qualified Domain Names
- **DNS Servers**: Root, primary, secondary, caching

### 🔹 Resolution Types:
- **Recursive**: Server resolves query fully
- **Iterative**: Client queries multiple servers
- **Caching**: Stores responses for faster lookup

---

## 📁 Lecture 4: Application Layer (2)

### 🔹 HTTP (Hypertext Transfer Protocol):
- **Stateless protocol** using TCP (port 80)
- **Methods**: GET, POST, PUT, HEAD, etc.
- **Status Codes**: 200 OK, 404 Not Found, 500 Server Error, etc.
- **Headers**: General, request, response, entity
- **Cookies**: Maintain state across sessions

### 🔹 FTP (File Transfer Protocol):
- Uses two TCP connections: control (port 21), data (port 20)
- **Modes**: Active vs. Passive

### 🔹 SMTP (Simple Mail Transfer Protocol):
- Email delivery to server
- **Access Protocols**: POP, IMAP, HTTP

### 🔹 Web Documents:
- **Static**: Pre-built (HTML, XML)
- **Dynamic**: Server-generated (CGI, JSP, ASP)
- **Active**: Client-side scripts (Java applets, JavaScript)

---

## 📁 Lecture 6: Transport Layer (2) – TCP

### 🔹 TCP Features:
- **Connection-oriented**, reliable, full-duplex
- **Flow Control**: Prevents receiver overload
- **Error Control**: Retransmission of lost/corrupted segments
- **Congestion Control**: Adjusts sending rate based on network load

### 🔹 Segment Structure:
- Header (20–60 bytes) + Data
- **Flags**: URG, ACK, PSH, RST, SYN, FIN

### 🔹 Connection Management:
- **3-Way Handshake**: SYN → SYN-ACK → ACK
- **Data Transfer**: Segments with sequence/ack numbers
- **Connection Termination**: FIN → FIN-ACK → ACK

### 🔹 TCP vs. UDP:
| Feature        | TCP                  | UDP                  |
|----------------|----------------------|----------------------|
| Connection     | Connection-oriented  | Connectionless       |
| Reliability    | Reliable             | Unreliable           |
| Error Control  | Yes                  | Optional             |
| Speed          | Slower               | Faster               |
| Overhead       | Higher (20–60 bytes) | Lower (8 bytes)      |
| Use Cases      | HTTP, FTP, SMTP      | DNS, DHCP, VoIP      |

---


## 📁 Lecture 7: Network Layer

### 🔹 Key Concepts:
- **Switching**:  
  - **Circuit Switching**: Dedicated path for entire message.  
  - **Packet Switching**: Message divided into packets (datagrams).  
- **IP Header Format**:  
  - 20–60 bytes; includes Version, HLEN, TOS, Total Length, Identification, Flags, Fragment Offset, TTL, Protocol, Checksum, Source/Dest IP.  
- **Fragmentation**:  
  - Packets split if larger than MTU; uses Identification, Flags (DF, MF), Fragment Offset.  
- **Forwarding & Routing**:  
  - **Forwarding**: Moving packet to next hop.  
  - **Routing**: Determining path using algorithms.  
- **Routing Algorithms**:  
  - **Distance Vector (Bellman-Ford)**: Each router shares its DV table.  
  - **Link State (Dijkstra)**: All routers know full topology.  
- **Autonomous Systems (AS)**:  
  - **Intradomain**: RIP, OSPF  
  - **Interdomain**: BGP  

---

## 📁 Lecture 8: Data Link Layer

### 🔹 Key Functions:
- **Framing**: Pack bits into frames; methods:  
  - Fixed-size, Variable-size  
  - Delimiting: Character count, Byte stuffing, Bit stuffing  
- **Flow Control**:  
  - **Stop-and-Wait**: Send one frame, wait for ACK.  
  - **Go-Back-N**: Send multiple frames; retransmit all after lost frame.  
  - **Selective Repeat**: Retransmit only lost frames.  
- **Error Control**:  
  - **Parity Check**: Even/odd parity.  
  - **Checksum**: One’s complement sum.  
  - **CRC**: Binary division.  
  - **Hamming Code**: Single-error correcting code.  
- **MAC Protocols**:  
  - **Channel Partitioning**: FDMA, TDMA, CDMA  
  - **Random Access**: ALOHA, CSMA, CSMA/CD, CSMA/CA  
  - **Controlled Access**: Polling, Token passing  
- **Wireless Issues**:  
  - Hidden terminal → solved with RTS/CTS  
  - Exposed terminal → solved with synchronization  

---

## 📁 Lecture 9: Physical Layer

### 🔹 Key Concepts:
- **Data & Signals**:  
  - **Analog**: Continuous (e.g., sound waves).  
  - **Digital**: Discrete (e.g., binary data).  
- **Transmission Impairments**:  
  - **Attenuation**: Loss of signal strength → use amplifiers.  
  - **Distortion**: Change in signal shape.  
  - **Noise**: Thermal, induced, crosstalk, impulse.  
- **Digital Transmission**:  
  - **Synchronous**: Continuous bit stream; receiver groups bits.  
  - **Asynchronous**: Start/stop bits per byte.  
- **Line Coding**: Convert digital data to digital signals.  
  - **Unipolar**: 1 = high, 0 = zero.  
  - **Polar**:  
    - NRZ-L, NRZ-I  
    - RZ: returns to zero mid-bit  
    - Biphase: Manchester, Differential Manchester  
  - **Bipolar**: AMI, Pseudoternary (3 voltage levels)  

---

## 🧠 Quick Recap:
- **Networking** involves communication between devices via wired/wireless channels.
- **Layered models** (OSI/TCP/IP) simplify design and interoperability.
- **Application layer** protocols (HTTP, DNS, FTP, SMTP) enable user services.
- **Transport layer** (TCP/UDP) ensures reliable/end-to-end communication.
- **TCP** is reliable and connection-oriented; **UDP** is fast and connectionless.
- **Network Layer**: Handles packet forwarding, routing, and fragmentation.  
- **Data Link Layer**: Manframes, flow/error control, MAC protocols.  
- **Physical Layer**: Transmits raw bits; handles signals, impairments, and encoding.  

---

**Feel Free to Fork and Contribute**
      - Prepared by Md. Mahmudul Hasan Rabbi

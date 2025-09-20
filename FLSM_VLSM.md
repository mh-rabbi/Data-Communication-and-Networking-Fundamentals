# FLSM and VLSM Subnetting: Concepts and Step-by-Step Methods

 **I have made videos to solve math problems with these two approach** -
  - **FLSM - [https://youtu.be/H3Li44w2mE0](https://youtu.be/rZK0GaQOIog)**
  - **VLSM - [https://youtu.be/H3Li44w2mE0](https://youtu.be/H3Li44w2mE0)**

## Introduction

**Subnetting** is the process of dividing a large network into smaller, manageable subnetworks (subnets). This technique optimizes IP address usage, improves traffic management, and isolates broadcast domains. For example, a `/24` network can be split into two `/25` subnets.

### Key Terminology:
- **Network ID**: First IP address in a subnet.
- **Broadcast ID**: Last IP address in a subnet.
- **First Host ID**: First usable IP (Network ID + 1).
- **Last Host ID**: Last usable IP (Broadcast ID - 1).
- **IP Addresses**: Total number of IPs in a subnet.

---

## Approaches to Subnetting

### 1. FLSM (Fixed Length Subnet Mask)
In FLSM, all subnets use the same subnet mask, meaning each subnet has an equal number of hosts.

#### Advantages:
- Simple to plan and implement.
- Easy routing and summarization.
- Ideal for networks with uniform host requirements.

#### Disadvantages:
- Wastes IP addresses if host needs vary.
- Inflexible for dynamic networks.

#### Characteristics:
| Feature        | Description                          |
|----------------|--------------------------------------|
| Subnet Size    | Same for all subnets                 |
| Subnet Mask    | Fixed across subnets                 |
| Simplicity     | Easy to calculate and manage         |
| IP Usage       | Potentially inefficient              |

#### Step-by-Step FLSM Method:
1. **Identify the network address** (e.g., `192.168.1.0/24`).
2. **Determine bits available for subnetting** (e.g., for `/24`, 8 host bits).
3. **Calculate bits needed for subnets**:
   - Required subnets = \( n \), find \( m \) such that \( 2^m \geq n \).
   - Subnet mask = original mask + \( m \).
4. **Use remaining bits for hosts**:
   - Hosts per subnet = \( 2^{(h)} - 2 \), where \( h \) = remaining host bits.
5. **Define subnets**:
   - Increment the subnet portion of the IP address by \( 2^h \).


More casually if I say -
- Identify the network address from the given ip. 
- Calculate how much bits left for subnetting. 
- Calculate how much bits needed for subnetting (from leftmost bits of the bits will be used for subnetting and rightmost bits will be used for hosts of subnets). 
- Use rest bits for host addresses. 
- For each subnetwork, sub-net bits must be changed

#### Example:
Network: `192.168.1.0/24`, need 4 subnets.
- \( m = 2 \) (since \( 2^2 = 4 \)), new mask = `/26`.
- Host bits = 6, hosts per subnet = \( 2^6 - 2 = 62 \).
- Subnets:
  - `192.168.1.0/26`
  - `192.168.1.64/26`
  - `192.168.1.128/26`
  - `192.168.1.192/26`

---

### 2. VLSM (Variable Length Subnet Mask)
VLSM allows subnets of different sizes by applying variable subnet masks. This maximizes IP efficiency.

#### Advantages:
- Efficient IP utilization.
- Flexible for real-world networks with varying host needs.
- Supports hierarchical design.

#### Disadvantages:
- Complex to plan and manage.
- Requires careful calculation.

#### Characteristics:
| Feature        | Description                          |
|----------------|--------------------------------------|
| Subnet Size    | Variable per subnet                  |
| Subnet Mask    | Different masks for different subnets|
| IP Utilization | Highly efficient                     |
| Complexity     | More complex planning                |

#### Step-by-Step VLSM Method:
1. **Identify the network address** (e.g., `192.168.1.0/24`).
2. **List subnets in descending order of host requirements**.
3. **Allocate largest subnet first**:
   - For a subnet requiring \( H \) hosts, find \( h \) such that \( 2^h - 2 \geq H \).
   - Subnet mask = \( 32 - h \).
4. **Assign the subnet** and mark it as used.
5. **Repeat for next largest subnet** from the remaining address space.
6. **Continue until all subnets are allocated**.

More casually if I say -
- Identify the network address from the given ip. 
- Calculate how much bits left for subnetting. 
- Sort by the no. of hosts needed for each subnet in descending order. 
- Start from rightmost bit and calculate how much bits needed for all hosts of a network. 
- Rest bits are for sub-network addresses. 
*for each subnetwork, sub-net bits must be changed. Change the rightmost bit of previous subnet 
bits to 1 and rest keep it as 0.

#### Example:
Network: `192.168.1.0/24`, subnets:
- Engineering: 60 hosts
- Sales: 40 hosts
- HR: 20 hosts
- Accounting: 10 hosts

**Steps**:
1. **Engineering (60 hosts)**:
   - \( h = 6 \) (since \( 2^6 - 2 = 62 \geq 60 \)), mask = `/26`.
   - Subnet: `192.168.1.0/26` (Range: `.1` to `.62`).

2. **Sales (40 hosts)**:
   - \( h = 6 \) (62 hosts), mask = `/26`.
   - Next available: `192.168.1.64/26` (Range: `.65` to `.126`).

3. **HR (20 hosts)**:
   - \( h = 5 \) (30 hosts), mask = `/27`.
   - Next available: `192.168.1.128/27` (Range: `.129` to `.158`).

4. **Accounting (10 hosts)**:
   - \( h = 4 \) (14 hosts), mask = `/28`.
   - Next available: `192.168.1.160/28` (Range: `.161` to `.174`).

Remaining space: `192.168.1.176/28` to `192.168.1.255`.

---

## Discussion

- **FLSM** is best for environments with uniform host requirements (e.g., labs). It is simple but may waste IPs.
- **VLSM** is ideal for real-world networks with varying host needs. It maximizes efficiency but requires careful planning.

## Conclusion

Both FLSM and VLSM are essential for network design:
- Use **FLSM** for simplicity and uniformity.
- Use **VLSM** for efficiency and flexibility.

Mastering both techniques ensures optimal IP management and scalable network design.

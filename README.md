# 🏢 Enterprise Network Design & Simulation Case Study: Oscorp Trading Floor

> A comprehensive, enterprise-grade 3-floor network architecture and simulation designed for Oscorp's trading floor support center, featuring advanced hierarchical routing, granular security segmentation, and high-availability infrastructure built in **Cisco Packet Tracer**.

---

## 📋 Executive Summary

Following a recent corporate expansion, Oscorp required a secure, scalable, and future-proofed network infrastructure for its relocating trading floor support center (500+ employees across 6 specialized departments and a high-security server room). This project provides a fully simulated logical and physical deployment adhering to strict enterprise design principles, including multi-tier redundancy, fault-tolerant WAN connectivity, and strict departmental isolation.

---

## 🏗️ Architectural Topology & Layout

The network is structured around a **Hierarchical Three-Tier Model** (Core, Distribution, and Access Layers) spread across a modern three-story building layout.

```
                  [ ISP 1 ]             [ ISP 2 ]
                     \                     /
                   [ Core Router 1 ] -- [ Core Router 2 ]
                           \             /
                         [ Multilayer Switch 1 ]
                                   |
                         [ Multilayer Switch 2 ]
                           (Inter-VLAN Routing)
                                   |
      +----------------------------+----------------------------+
      |                            |                            |
[ Floor 1 Access Switch ]    [ Floor 2 Access Switch ]    [ Floor 3 Access Switch ]
  - Sales & Marketing          - Finance & Accounts         - ICT Department
  - Human Resources & Logistics - Admin & PR                - Server Room (DHCP/Core)
```

### Building & Departmental Breakdown
* **First Floor:**
  * **Sales & Marketing Department** (100 Users)
  * **Human Resources & Logistics Department** (100 Users)
* **Second Floor:**
  * **Finance & Accounts Department** (100 Users)
  * **Administrator & Public Relations Department** (100 Users)
* **Third Floor:**
  * **ICT Department** (120 Users)
  * **Server Room** (12 Critical Infrastructure Devices)

---

## ⚙️ Key Technical Features & Implementation

### 1. High Availability & Redundancy
* **Core Redundancy:** Deployed dual core routers and dual redundant multilayer switches to eliminate single points of failure (SPOF) across the core and distribution layers.
* **Dual-ISP WAN Edge:** Connected routers across redundant public upstream providers utilizing static public IP blocks (`/30` subnets: `195.136.17.0/30`, `195.136.17.4/30`, `195.136.17.8/30`, and `195.136.17.12/30`) to ensure uninterrupted internet gateway access and failover capabilities.

### 2. Network Segmentation & VLAN Architecture
* Built on the base network block **`192.168.10.0`**, utilizing precise subnetting (VLSM) to accommodate departmental scaling.
* Every department resides in its own **isolated Virtual Local Area Network (VLAN)** and unique subnet to restrict broadcast domains and mitigate lateral threat movement.
* **Inter-VLAN Routing:** Configured on the core multilayer switches to enable secure, high-speed routing between distinct departmental subnets.

### 3. Core Services & Wireless Integration
* **Automated IP Allocation (DHCP):** Centralized DHCP servers deployed in the third-floor server room dynamically provision IP configurations across all departmental hosts.
* **Enterprise Wireless:** Integrated secure wireless access points across all departmental zones to support mobile office environments.

### 4. Device Hardening & Security Baseline
* Standardized administrative access configurations across all network equipment:
  * Secure console and VTY line passwords.
  * Custom MOTD (Message of the Day) warning banners.
  * Disabled unused IP domain lookups and secured management planes.

---

## 🛠️ Tools & Technologies Used
* **Simulation Software:** Cisco Packet Tracer
* **Protocols & Standards:** VLANs, Inter-VLAN Routing, Static & Dynamic Routing, DHCP, Spanning Tree Protocol (STP), OSPF.
* **IP Addressing:** IPv4 (Private RFC 1918 space + Public `/30` WAN blocks).

---

## 🚀 Getting Started with the Simulation

1. Ensure you have **Cisco Packet Tracer** installed (Recommended version: 8.0 or higher).
2. Clone this repository or download the `.pkt` project file:
   ```bash
   git clone https://github.com/GGovindkrishna/oscorp-network-design.git
   ```
3. Open the file `Oscorp_Network_Design.pkt` in Cisco Packet Tracer.
4. Verify connectivity by running ping tests across different departmental subnets or checking the DHCP lease tables on client hosts.

---

## 📄 License
This project is open-source and available under the [MIT License](LICENSE).

# Examine NAT on a Wireless Router — Cisco Packet Tracer

## 📌 Description
This lab demonstrates **NAT (Network Address Translation)** on a home wireless router, showing how private (internal) IP addresses are translated into a public (external) IP address when traffic leaves the local network toward the internet.

## 🗂️ Topology
```
PC1, PC0, PC2, PC3  →  Wireless Router  →  Cluster (ISP Cloud)  →  ciscolearn.nat.com (Web Server)
```

- 4 PCs connected to the wireless router's LAN (DHCP clients)
- Wireless router's WAN/Internet interface connected through a simulated ISP cloud
- A remote web server (`ciscolearn.nat.com`) representing an external destination

## ⚙️ Configuration Steps
1. Checked the router's **Internet Connection** status page (`Status_Router.asp`):
   - Connection Type: Automatic Configuration – DHCP
   - Public/WAN IP obtained from ISP: `209.165.200.227`
2. Checked the router's **Local Network** status page (`Status_Lan.asp`):
   - Router LAN IP: `192.168.1.1`
   - DHCP Server enabled, range `192.168.1.100 – 192.168.1.149`
3. Verified DHCP reservation table showing leased LAN IPs and MAC addresses.
4. Confirmed each PC (PC0–PC3) received a private IP via DHCP:
   - PC0: `192.168.1.101`
   - PC1: `192.168.1.100`
   - PC2: `192.168.1.102`
   - PC3: `192.168.1.103`
5. Enabled **HTTP/TCP** event filters in Simulation mode.
6. Created a **Complex PDU** (HTTP request) from PC1 to the external server `209.165.200.228`, port 80.
7. Ran the simulation and traced the packet through: PC1 → Wireless Router → Cluster (ISP) → Web Server.
8. Inspected the packet at each hop to observe NAT translation.

## 🔍 NAT in Action — PDU Inspection

| Location                | Source IP        | Destination IP     |
|--------------------------|-------------------|----------------------|
| At PC1 (outbound)         | `192.168.1.100`   | `209.165.200.228`    |
| At Wireless Router (inbound, LAN side) | `192.168.1.100`   | `209.165.200.228`    |
| At Wireless Router (outbound, WAN side) | **`209.165.200.227`** | `209.165.200.228`    |

➡️ The router **translated the private source IP** (`192.168.1.100`) **into its own public IP** (`209.165.200.227`) before forwarding the packet to the internet — this is **NAT / PAT (Port Address Translation)** at work.

## ✅ Activity Results
- Activity completed successfully.
- All 4 PCs (PC0–PC3) passed the "IP Address Correct" assessment check.

## 🧠 Key Concepts
- **NAT (Network Address Translation)**: translates private IP addresses to a public IP address so internal devices can communicate with external networks.
- **PAT (Port Address Translation)**: allows many internal devices to share a single public IP by using different source ports.
- Private IP ranges (e.g., `192.168.1.0/24`) are not routable on the internet — NAT solves this by masking them behind a public IP.
- This is the same mechanism used by home routers to let multiple devices share one internet connection.

## 🛠️ Tools Used
- Cisco Packet Tracer (Simulation Mode, PDU inspection)

## 📁 Files
- `Examine_NAT_on_a_Wireless_Router_Instructions.pka` — Packet Tracer activity file
- Screenshots of configuration, DHCP tables, and PDU traces

## 👤 Author
Networking lab exercise — part of my hands-on CCNA Packet Tracer series.

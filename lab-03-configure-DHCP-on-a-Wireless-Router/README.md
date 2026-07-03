# Configure DHCP on a Wireless Router — Cisco Packet Tracer

## 📌 Description
This project demonstrates how to configure a **DHCP server on a wireless router** using **Cisco Packet Tracer**, and how to verify that connected hosts correctly receive their IP configuration.

The topology consists of:
- 1 DHCP-enabled wireless router
- 3 PCs (PC0, PC1, PC2) connected via FastEthernet

## 🗂️ Topology
```
                [DHCP Enabled Router]
                 /        |        \
              PC0        PC1       PC2
```

## ⚙️ Configuration Steps
1. Accessed the router's web configuration page (`http://192.168.5.1`) from PC0.
2. Under **Network Setup**, set the Router IP to `192.168.5.1` with subnet mask `255.255.255.0`.
3. Enabled the **DHCP Server**:
   - Start IP Address: `192.168.5.126`
   - Maximum number of users: `75`
   - IP Address Range: `192.168.5.126 – 192.168.5.200`
4. Set each PC's IP Configuration mode to **DHCP** (instead of Static).
5. Verified IP assignment on each client using `ipconfig`.
6. Tested connectivity with `ping` between hosts and the gateway.

## ✅ Verification Results

| Device | IPv4 Address    | Subnet Mask     | Default Gateway |
|--------|-----------------|------------------|------------------|
| PC0    | 192.168.5.128   | 255.255.255.0    | 192.168.5.1      |
| PC2    | 192.168.5.127   | 255.255.255.0    | 192.168.5.1      |

**Ping tests:**
```
C:\>ping 192.168.5.1
Reply from 192.168.5.1: bytes=32 time<1ms TTL=255   (x4)
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)

C:\>ping 192.168.5.126
Reply from 192.168.5.126: bytes=32 time<1ms TTL=128 (x4)
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)

C:\>ping 192.168.5.127
Reply from 192.168.5.127: bytes=32 time<1ms TTL=128 (x4)
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
```

All hosts successfully obtained an IP address via DHCP and can reach the gateway and each other with **0% packet loss**.

## 🧠 Key Concepts
- **DHCP (Dynamic Host Configuration Protocol)**: automatically assigns IP addresses, subnet masks, and default gateways to hosts on a network.
- **DORA process**: Discover → Offer → Request → Acknowledge.
- Benefits of DHCP over static addressing: reduced configuration errors, centralized IP management, scalability.

## 🛠️ Tools Used
- Cisco Packet Tracer

## 📁 Files
- `Configure_DHCP_on_a_Wireless_Router.pka` — Packet Tracer activity file
- Screenshots of configuration and verification steps

## 👤 Author
Networking lab exercise — feel free to fork and experiment with different DHCP pool ranges or additional VLANs.

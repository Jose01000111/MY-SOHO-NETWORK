# 🧰 SOHO Network Setup — Hardware Inventory & Topology

This post documents the initial setup of my Small Office/Home Office (SOHO) network for a 28-day lab project. It includes the hardware inventory with labeled devices and a logical network topology diagram.

---

## Hardware Inventory

| Device Name                 | Model Number   | Role                     | Notes                   |
|----------------------------|----------------|--------------------------|-------------------------|
| Reolink Security Camera    | Reolink RLC-520A | PoE Camera               | Mounted on front door   |
| TP-Link EAP245 V3 AP       | EAP245 V3      | PoE Access Point          | WPA3 enabled            |
| TP-Link ER707-M2 VPN Router| ER707-M2       | VPN Router / Firewall    | Multi-Gig               |
| TP-Link TL-SF1005P PoE Switch | TL-SF1005P | PoE Switch                | Connected to Camera + AP|
| TP-Link TL-SG105 Switch    | TL-SG105       | Gigabit Switch            | Unmanaged               |
| Canon PIXMA TS7720 Printer | TS7720         | Printer                   | USB & Network capable   |

---

# 🧰 SOHO Network Hardware List

## 🎥 **Reolink Security Camera** — PoE Camera

<img width="508" height="615" alt="9IEhax8" src="https://github.com/user-attachments/assets/7abe8f4e-863e-4978-8edf-d23c388451cd" />
  
## 📡 **TP-Link EAP245 V3 AP** — PoE Wireless Access Point  

<img width="889" height="608" alt="ZW3Dvgy" src="https://github.com/user-attachments/assets/de77adc9-a7c7-47a8-b3ac-4c07dec33e6f" />

## 🌐 **TP-Link ER707-M2 Router** — VPN Router / Firewall / Load Balancer  

<img width="886" height="521" alt="nfUycV1" src="https://github.com/user-attachments/assets/739b0085-9e1a-4e52-8bab-e725bfb1d811" />

## 🔌 **TP-Link TL-SF1005P Switch** — PoE Switch  

<img width="466" height="525" alt="MQ1AvON" src="https://github.com/user-attachments/assets/f14b5592-1d60-4fc3-9a78-15d3b8ba1424" />

## 🔗 **TP-Link TL-SG105 Switch** — Unmanaged Gigabit Switch  

<img width="571" height="548" alt="1Z3IZnJ" src="https://github.com/user-attachments/assets/5b877aef-594e-43d6-b3ec-ff557fedd6ae" />

## 🖨️ **Canon PIXMA TS7720 Printer** — Network Printer  

<img width="950" height="468" alt="VQuMMAP" src="https://github.com/user-attachments/assets/c99989a1-90e5-4546-b6ff-fde442406c4b" />

---

## Network Topology Diagram

```plaintext
                    [Internet]
                        |
              +---------------------+
              | TP-Link ER707-M2 VPN|
              |   Router/Firewall   |
              +----------+----------+
                         |
       +-----------------+-----------------+
       |                                   |
+--------------+                   +------------------+
| TL-SF1005P   |                   | TL-SG105 Switch  |
| PoE Switch   |                   | (Unmanaged)      |
+------+-------+                   +--------+---------+
       |                                     |
   +---+---+                          +------+------+
   |       |                          |             |
[Reolink   |                      [Canon PIXMA  Windows PC]
Camera]    |                       TS7720 Printer]    |
           |                                            |
    [TP-Link EAP245 V3 AP]                        [RHEL 9 VM]
    (PoE Access Point)

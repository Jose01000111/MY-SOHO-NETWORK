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
    [TP-Link EAP245 V3 AP]                        [RHEL 9 System]
    (PoE Access Point)

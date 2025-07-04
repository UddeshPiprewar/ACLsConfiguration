# ACLsConfiguration
𝗩𝗟𝗔𝗡 𝗶𝗻 𝗔𝗰𝘁𝗶𝗼𝗻 | 𝗔𝗱𝘃𝗮𝗻𝗰𝗲𝗱 𝗡𝗲𝘁𝘄𝗼𝗿𝗸 𝗦𝗲𝗴𝗺𝗲𝗻𝘁𝗮𝘁𝗶𝗼𝗻 𝘄𝗶𝘁𝗵 𝗔𝗖𝗟𝘀 

I recently worked on a detailed VLAN lab that demonstrates efficient network segmentation using 4 switches and 8 VLANs. This setup simulates a real-world enterprise network where different teams are logically separated for better structure and control.

🔧 Lab Overview

4 Switches, 8 VLANs, 32 Devices, 2 Logical Groups:

## 👥 VLAN Grouping
```bash
## 🔧 Technical Group (Lower Side)
- VLAN 10: Developers  
- VLAN 30: Network Engineers  
- VLAN 50: Database Engineers  
- VLAN 70: Software Testers
```
```bash
## 💼 Non-Technical Group (Upper Side)
- VLAN 20: Managers  
- VLAN 40: Marketing  
- VLAN 60: Sales  
- VLAN 80: HR
```
🔀 Communication Rules
  ✅ Devices within the same group can communicate freely
  🚫 Communication between technical and non-technical groups is restricted

This was achieved using Access Control Lists (ACLs) on a Layer 3 device.

🛠 ACL Configuration (Simplified)
```bash
##Allow internal group communication (example)
access-list 100 permit ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255

##Deny cross-group access
access-list 100 deny ip 192.168.10.0 0.0.0.255 192.168.50.0 0.0.0.255

##Apply the ACL to the VLAN interface
interface vlan 1
ip access-group 100 in
```
🧪 Key Points

Configure trunk ports correctly to carry all VLANs

Use Layer 3 routing to enable inter-VLAN communication

Always test access rules with tools like ping or traceroute

# Track 1 — Lab Topics

รายการด้านล่างเป็น Selected Activities สำหรับ Workshop 1 วัน โดยจัดกลุ่มให้ทำงานต่อเนื่องจากระบบเดียวกัน ไม่ใช่ 12 Labs ที่ต้องเริ่มจาก OS เปล่าทั้งหมด

![Track 1 — Logical Roles](images/lab-architecture.svg)

## 01 — AD Foundation (Objectives 01–03)

- **โจทย์:** สร้าง Domain ใหม่และเพิ่ม Domain Controller ให้ทำงานร่วมกัน
- **กิจกรรม:** Promote First DC, Manage FSMO, Configure AD Sites/Subnets, Add Additional DC, Create AD Users/Groups
- **ตรวจผล:** `netdom query fsmo`, `dcdiag`, `repadmin /replsummary`, Sites และ Security Principals
- **Delivery:** Guided/Staged Setup สำหรับการ Promote และ Restart

## 02 — Group Policy and Remote Management (Objectives 04–05)

- **โจทย์:** ตั้ง Domain-based Policy และบริหารเครื่องจากส่วนกลาง
- **กิจกรรม:** Implement GPO, Install Windows Admin Center
- **ตรวจผล:** `gpresult` และ Remote Server Connection ผ่าน WAC
- **Delivery:** Hands-on + Prepared Management VM

## 03 — DNS and DHCP Failover (Objectives 09–10)

![Lab — DNS and DHCP](images/lab-03-dns-dhcp.svg)

- **โจทย์:** ให้ Client ได้ IP และ Resolve ชื่อได้ พร้อมมี DHCP Partner Server
- **กิจกรรม:** Configure DNS และ DHCP Failover บน DHCP Servers 2 ตัว
- **ตรวจผล:** DNS Queries, Scope/Failover Relationship, Leases
- **Delivery:** Guided (DHCP Roles/Network เตรียมไว้ล่วงหน้า)

## 04 — File Services (Objective 12)

![Lab — File Services](images/lab-04-file-services.svg)

- **โจทย์:** Share Files ตามสิทธิ์และรวม Namespace ของ File Shares
- **กิจกรรม:** Share Permissions, FSRM, DFS Namespace
- **ตรวจผล:** User Access Test, FSRM Rules, DFS Path
- **Delivery:** Hands-on/Guided; DFS Replication เป็น Extension เท่านั้น

## 05 — Security (Objective 14)

![Lab — Windows LAPS](images/lab-02-gpo-laps.svg)

- **โจทย์:** ปกป้อง Server และลดการใช้ Local Administrator Password ร่วมกัน
- **กิจกรรม:** Windows Server Hardening Controls, Implement Windows LAPS
- **ตรวจผล:** Policy/Control Status, LAPS Backup/Permissions
- **Delivery:** Hands-on โดย Instructor เตรียม Schema/Permissions ไว้

## 06 — Performance Monitoring (Objective 16)

![Lab — Diagnostics](images/lab-07-monitoring.svg)

- **กิจกรรม:** Configure PerfMon Counters และ Data Collector Set
- **ตรวจผล:** มี Collected Data ที่เปิดอ่านและตีความเบื้องต้นได้

## 07 — Basic Troubleshooting (Objective 17)

- **กิจกรรม:** Network Connectivity, DNS Name Resolution, Windows Time Synchronization
- **ตรวจผล:** `Test-NetConnection`, `Resolve-DnsName`, `w32tm` และ Logs ที่เกี่ยวข้อง

## 08 — AD Recovery / Health (Objective 18)

![Lab — AD DS](images/lab-01-ad-ds.svg)

- **กิจกรรม:** Enable AD Recycle Bin, Restore Test Object และ Mini AD Health Check
- **ตรวจผล:** Restored Object ถูกต้อง, `dcdiag`/`repadmin` และ Event Logs

---

[Schedule](workshop-plan.md) · [Selected 18 Objectives](lab-catalog.md) · [Track 2](advanced-track.md)

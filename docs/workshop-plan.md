# Track 1 — Administration Workshop (09:00–17:00)

**Project:** Build and Manage a Windows Server Domain Infrastructure

![Track 1 — Lab Topology](images/lab-architecture.svg)

## Schedule (Tentative)

| เวลา | Lab Session | Selected Objectives |
|---|---|---|
| 09:00–09:20 | Scenario, Access Check, Roles and Requirements | Intro |
| 09:20–10:25 | 01 — AD Foundation: First DC, FSMO, Sites, Additional DC, Users/Groups | 01–03 |
| 10:25–11:00 | 02 — GPO and Windows Admin Center | 04–05 |
| 11:00–12:00 | 03 — DNS and DHCP Failover | 09–10 |
| 12:00–13:00 | Lunch | — |
| 13:00–14:10 | 04 — Share Permissions, FSRM and DFS | 12 |
| 14:10–14:55 | 05 — Server Hardening and Windows LAPS | 14 |
| 14:55–15:10 | Break | — |
| 15:10–15:45 | 06 — Performance Monitoring | 16 |
| 15:45–16:20 | 07 — Connectivity, DNS and Time Troubleshooting | 17 |
| 16:20–17:00 | 08 — AD Recycle Bin, Mini AD Health Check and Final Review | 18 |

**รวม:** 480 นาที รวมพัก 75 นาที เหลือ 405 นาทีสำหรับการเรียนและ Lab

การ Promote DC, DHCP Failover และ DFS ต้องใช้ Prepared Images/Checkpoints และอาจมี Guided Steps หรือ Demo ในบางส่วน ตารางนี้เป็นเป้าหมายที่ต้องทดลองทำจริงแบบจับเวลาก่อนเปิดรุ่น

## Requirements and Validation

- AD DS: ตรวจ Domain Services, Additional DC, FSMO และ Sites
- DNS/DHCP: ยืนยัน Name Resolution และ Lease/Failover Configuration
- File Services: ตรวจ Share Permissions, FSRM และ DFS Namespace
- Security: ตรวจ GPO/Windows LAPS และ Hardening Controls
- Diagnostics: ใช้ PerfMon, Network/DNS/Time Checks, AD Recycle Bin และ Mini Health Check

แยก Logical Roles ใน Diagram เพื่ออธิบาย Dependencies แม้ใน Lab จริงบาง Roles จะรวมอยู่บน Guest VM เดียวกัน

[Lab Topics](lab-briefs.md) · [Course Outline](course-outline.md) · [Logical Roles](lab-topology.md)

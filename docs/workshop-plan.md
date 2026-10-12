# Track 1 — Onsite Workshop (09:00–17:00)

**Scenario:** Deploy and Secure a Hybrid Windows Server Infrastructure

บริษัทต้องการเพิ่ม Domain Controller, ควบคุมการตั้งค่าเครื่อง Client, ให้บริการ File Share พร้อมสิทธิ์การเข้าถึงที่เหมาะสม และจัดการ On-premises Windows Server ผ่าน Azure

![Track 1 Topology](images/lab-architecture.svg)

## ตาราง Workshop

| เวลา | หัวข้อ | ผู้เรียนจะได้ทำอะไร |
|---|---|---|
| 09:00–09:20 | Architecture / Requirements | เข้าใจระบบที่ต้องสร้างและตรวจ Environment |
| 09:20–10:10 | Lab 01 — Active Directory | เพิ่ม DC และตรวจ Replication |
| 10:10–10:55 | Lab 02 — GPO & Windows LAPS | ตั้ง Policy และตรวจว่า Applied |
| 10:55–11:40 | Lab 03 — DNS & DHCP | ตั้ง Network Services และทดสอบจาก Client |
| 11:40–12:00 | Validation / Q&A | ตรวจระบบช่วงเช้า |
| 12:00–13:00 | Lunch | พักกลางวัน |
| 13:00–14:10 | Lab 04 — File Services | SMB Share, Share/NTFS Permissions, FSRM (ตามเวลา) |
| 14:10–14:45 | Lab 05 — Hyper-V (Conditional) | Virtual Switch / VM Checkpoint หรือ Demo สำรอง |
| 14:45–15:00 | Break | พัก |
| 15:00–15:45 | Lab 06 — Hybrid Management | Azure Arc และ Update Manager Assessment |
| 15:45–16:20 | Lab 07 — Monitoring | Event Logs, Performance และ Diagnostics |
| 16:20–17:00 | Final Challenge | วิเคราะห์และแก้โจทย์ Incident |

**เวลารวม:** 09:00–17:00 (480 นาทีรวมพัก) เวลาสอนและลงมือทำ 405 นาที

## วิธีเรียน

ใช้ชุด Lab VM เดียวกันตลอดวัน เพื่อให้เข้าใจ Dependency ของระบบ เช่น AD DS, DNS, File Services และ Group Policy ไม่ใช่เพียงทำตาม Wizard ทีละ Feature

แต่ละ Lab เริ่มจาก Requirement จากนั้น Configure, Validate และอธิบายผลการทดลอง

## ถ้า Infrastructure บางส่วนไม่พร้อม

Hyper-V เป็น Conditional Lab สามารถเปลี่ยนเป็น File Services Extension หรือ Azure File Sync Demo ได้ ส่วน Azure Update Assessment อาจใช้ผลที่เตรียมไว้ล่วงหน้าเพราะเวลาประมวลผลขึ้นอยู่กับ Service และ Environment

## รายละเอียด

- [Track 1 Course Outline](course-outline.md)
- [Lab Topics และ Expected Outcomes](lab-briefs.md)
- [Track 2 สำหรับ Advanced Features](advanced-track.md)

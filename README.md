# AZ-802 — Administering Windows Server

**Learn in the Cloud | Windows Server 2025**

หลักสูตรสำหรับผู้ดูแล Windows Server ที่ต้องการฝึกตั้งแต่ Configure ไปจนถึง Validate และ Troubleshoot ในสภาพแวดล้อม On-premises และ Hybrid

**รูปแบบ:** Recorded Video (เรียนล่วงหน้า) + Hands-on Project-based Onsite Workshop 1 วัน (09:00–17:00)

> Course Plan / Draft — เนื้อหาและ Lab อยู่ระหว่างพัฒนา ยังไม่ใช่เอกสารยืนยันวันเปิดอบรมหรือความพร้อมของวิดีโอทั้งหมด

## รูปแบบการเรียน

**Recorded Video:** Concepts และ Demo ตาม Skills Measured ของ AZ-802 ทั้ง 7 Domains เพื่อเตรียมพื้นฐานก่อน Onsite

**Onsite:** ทำ Project เดียวกันตลอดวัน ได้แก่ เพิ่ม Domain Controller, GPO/Windows LAPS, DNS/DHCP, File Services, Azure Arc, Monitoring และ Final Troubleshooting Challenge โดยมี Hyper-V เป็น Conditional Lab

ใช้ **Windows Server 2025** เป็น Lab Platform หลัก; หัวข้อสอบ AZ-802 ไม่ได้จำกัดเฉพาะ Windows Server 2025

## สิ่งที่จะได้ฝึก

- Deploy Additional Domain Controller และตรวจ Replication / FSMO / DNS
- Configure Group Policy และ Windows LAPS
- Configure DNS, DHCP และตรวจการทำงานจาก Windows Client
- Configure SMB Share และ Share/NTFS Permissions
- Connect On-premises Windows Server กับ Azure Arc และดู Update Assessment
- Monitor / Diagnose ด้วย Event Viewer, Performance Monitor และคำสั่ง Troubleshooting
- แก้ Incident จาก Requirements และหลักฐานที่ตรวจพบจริง

## Workshop Schedule

| เวลา | กิจกรรม |
|---|---|
| 09:00–09:20 | Requirements, Architecture, Lab Check |
| 09:20–10:10 | Lab 01 — Active Directory |
| 10:10–10:55 | Lab 02 — GPO & Windows LAPS |
| 10:55–11:40 | Lab 03 — DNS & DHCP |
| 11:40–12:00 | Validation & Q&A |
| 12:00–13:00 | Lunch |
| 13:00–14:10 | Lab 04 — File Services |
| 14:10–14:45 | Lab 05 — Hyper-V (Conditional) |
| 14:45–15:00 | Break |
| 15:00–15:45 | Lab 06 — Azure Arc & Update Manager |
| 15:45–16:20 | Lab 07 — Monitoring & Diagnostics |
| 16:20–17:00 | Final Troubleshooting Challenge |

Workshop เน้นให้ทำงานที่เลือกมาได้ **ครบและตรวจผลได้** ไม่ได้พยายามทำทุก Feature ใน Study Guide ภายในหนึ่งวัน

## เอกสารหลักสูตร

- [Course Outline](docs/course-outline.md) — กลุ่มเป้าหมาย, วัตถุประสงค์, Recorded Video Modules และ Mapping กับ AZ-802
- [Workshop Plan](docs/workshop-plan.md) — Project Scenario, ตารางเวลา, Priority และ Contingency Plan
- [Lab Briefs](docs/lab-briefs.md) — โจทย์, ขั้นตอนระดับงาน และ Validation ของ Lab 01–07 + Final Challenge
- [Instructor Setup](docs/instructor-setup.md) — Lab Topology, Prerequisites, Azure/Hyper-V Readiness และ Checklist เตรียมสอน

## Reference

[Microsoft Learn — Study guide for Exam AZ-802: Administering Windows Server](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802)

AZ-802 เป็นชื่อและขอบเขตของการสอบ Microsoft; หลักสูตรนี้เป็น Course Plan ของ Learn in the Cloud ไม่ใช่หลักสูตรที่ Microsoft ออกแบบหรือรับรองโดยตรง

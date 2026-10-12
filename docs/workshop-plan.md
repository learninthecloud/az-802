# Onsite Workshop Plan — 09:00–17:00

## Project Scenario

**Deploy and Secure a Hybrid Windows Server Infrastructure**

บริษัทมี AD DS อยู่แล้ว ต้องเพิ่ม Domain Controller, จัดการเครื่อง Client ผ่าน GPO, ให้บริการ DNS/DHCP, เปิดใช้ File Share อย่างปลอดภัย และเชื่อม Windows Server เข้ากับ Azure เพื่อดูแล Updates และตรวจสอบปัญหา

ผู้เรียนใช้ Environment เดิมตลอดวัน แต่ละ Lab เป็นส่วนหนึ่งของ Project เดียวกัน ไม่ใช่ Demo ที่ไม่เกี่ยวข้องกัน

### Lab Topology (Logical)

```text
                  Microsoft Azure
           Azure Arc / Update Manager
                        |
                  HTTPS / Internet
                        |
       +----------------+----------------+
       |       Isolated Lab Network      |
       |                                 |
       | DC01       DC02                 |
       | AD DS/DNS  Additional DC        |
       |                                 |
       | FS01             CLIENT01       |
       | SMB/FSRM/DHCP    Windows 11     |
       +---------------------------------+

       HV01 + Test VM = optional Hyper-V lab
```

- Domain ตัวอย่าง: **corp.example.test**
- Lab VMs: DC01, DC02, FS01, CLIENT01; เพิ่ม HV01 เฉพาะกรณีทำ Hyper-V
- FS01 ใช้ DHCP และ File Server รวมกันเฉพาะ Lab เพื่อประหยัด VM ไม่ใช่ข้อแนะนำให้รวม Role เหล่านี้ใน Production
- Azure Arc ใช้เชื่อม **on-premises VM** ไม่ใช่ Azure VM
- แต่ละ Pod ต้องแยก DHCP Broadcast Domain หรือ Network Segment ออกจาก Pod อื่นและเครือข่ายจริง

## ตารางสอน

| เวลา | นาที | เนื้อหา | ผลลัพธ์ |
|---|---:|---|---|
| 09:00–09:20 | 20 | Requirements / Architecture / Lab Check | เข้า Lab ได้ เข้าใจ Scenario |
| 09:20–10:10 | 50 | Lab 01 — AD DS | DC02 ทำงานและ Replication ผ่าน |
| 10:10–10:55 | 45 | Lab 02 — GPO + Windows LAPS | GPO Applied และ LAPS ทำงาน |
| 10:55–11:40 | 45 | Lab 03 — DNS + DHCP | Client ได้ IP และ Resolve Name ได้ |
| 11:40–12:00 | 20 | Morning Validation / Q&A | AD, DNS, DHCP และ GPO ผ่าน Checkpoint |
| 12:00–13:00 | 60 | Lunch | — |
| 13:00–14:10 | 70 | Lab 04 — File Services | Authorized/Unauthorized Access ถูกต้อง |
| 14:10–14:45 | 35 | Lab 05 — Hyper-V (Conditional) | Virtual Switch / Checkpoint หรือ Demo สำรอง |
| 14:45–15:00 | 15 | Break | — |
| 15:00–15:45 | 45 | Lab 06 — Azure Arc + Update Manager | Arc Connected และเห็น Assessment |
| 15:45–16:20 | 35 | Lab 07 — Monitoring / Diagnostic | เก็บหลักฐานจาก Log และ Commands |
| 16:20–17:00 | 40 | Final Challenge / Debrief | แก้ Incident พร้อม Validation |

**เวลารวม:** 480 นาที; พัก 75 นาที; เวลาสอน/ปฏิบัติ 405 นาที

ตารางนี้ทำได้เฉพาะกรณีเตรียม VM Images, Windows Updates, Network, Azure Permissions และ Prerequisites ที่ใช้เวลานานให้พร้อมก่อนวันเรียน

## Priority และขอบเขต

### Must do

- Promote Additional DC และตรวจสอบ Health/Replication
- Group Policy และ Windows LAPS
- DNS Records, DNS Resolution และ DHCP Scope/Reservation
- SMB Share, Share/NTFS Permissions และ Access Verification
- Azure Arc และ Update Manager Assessment
- Event Logs, Basic Performance Data และ Troubleshooting Challenge

### Should do

- Hyper-V Virtual Switch และ Checkpoint บน **Test VM** (ไม่ใช้ DC)
- FSRM Quota/File Screening หาก Lab 04 เดินตามเวลา
- Azure File Sync ผ่าน Demo หรือ Exercise ที่เตรียม Sync Group ไว้ก่อน

### Video/Optional เท่านั้นในรุ่น 1 วัน

- RODC, Cross-Forest Trust, AD Disaster Recovery แบบเต็มรูปแบบ
- Hyper-V Cluster/Replica และ Azure VM Migration
- Storage Spaces Direct, Storage Replica, SMB over QUIC, DFS Migration
- Advanced JEA, DNSSEC, System Insights และ Complex Azure Monitor Dashboards

## Contingency Plan

- ถ้า **Hyper-V/Nested Virtualization** ไม่พร้อม ให้ตัด Lab 05 และใช้ช่วงเวลานั้นกับ File Services หรือ Demonstration ของ Azure Files/File Sync
- ถ้า Azure Arc เชื่อมไม่ได้ในช่วงเรียน ให้ใช้ FS01 ตัวที่ Instructor เชื่อมไว้ก่อนแล้วฝึกตรวจ Resource/Update Assessment (พร้อมบันทึก Root Cause ของ Pod ที่เชื่อมไม่สำเร็จ)
- ถ้า Update Assessment ยังไม่จบ ให้ดูผล Assessment ที่เตรียมไว้ล่วงหน้า ไม่ต้องรัน Patch Installation ในห้อง
- ถ้า Lab ก่อนหน้าใช้เวลามาก ให้ลด Optional Features ก่อน อย่าตัด Final Challenge
- อาจารย์/ผู้ช่วยต้องมีวิธี Restore Pod กลับ Checkpoint ก่อนเริ่ม Lab สำคัญ

## Final Challenge

**Incident:** ผู้ใช้ Login Domain ได้ แต่เปิด `\\FS01\Departments` ไม่ได้ และบางเครื่องไม่ได้รับ GPO

ผู้เรียนต้องไล่ตรวจโดยใช้หลักฐานจากเครื่อง เช่น DNS, IP Configuration, Connectivity, AD/GPO, SMB และ NTFS Permissions (ลำดับตรวจสามารถเปลี่ยนได้ตามอาการที่พบ)

**สิ่งที่ต้องส่งก่อนจบ:**

1. Root Cause ที่ตรวจพบ พร้อมหลักฐานอย่างน้อย 2 จุด
2. การแก้ไขที่ทำจริง
3. ผลการ Validate จาก Client ทั้งผู้ใช้ที่มีสิทธิ์และไม่มีสิทธิ์
4. สิ่งที่ต้องทำเพิ่มหากเป็น Production Environment

**เกณฑ์ผ่าน:** ระบุ Root Cause ถูกต้อง, แก้ปัญหาได้, ยืนยันผลหลังแก้ และไม่เปิดสิทธิ์กว้างเกินจำเป็น

## ก่อนเข้าเรียน

- ดู Recorded Video ใน Module ที่เกี่ยวข้อง หรือทำ Pre-work ที่กำหนด
- ทบทวน DNS, DHCP, AD DS, SMB Permissions และ PowerShell เบื้องต้น
- เตรียม Laptop ที่เข้าถึง Lab Portal และ Azure Portal ได้
- ทดสอบ Browser, MFA, Remote Desktop/Console Access และบัญชี Lab ล่วงหน้า

รายละเอียดงานในแต่ละช่วงดู [Lab Briefs](lab-briefs.md) และสิ่งที่ทีมผู้สอนต้องเตรียมดู [Instructor Setup](instructor-setup.md)

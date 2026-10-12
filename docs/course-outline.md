# Track 1 — Windows Server Administration

**Learn in the Cloud | AZ-802: Administering Windows Server**

**รูปแบบ:** Recorded Video/Pre-work + Onsite Workshop 1 วัน (09:00–17:00)  
**Lab Platform:** Windows Server 2025, Windows 11 และ Microsoft Azure  
**ราคาเสนอ:** 5,750 บาท หรือแพ็กเกจ 2 Tracks ราคา 8,625 บาท

![Track 1 — Windows Server Lab Architecture](images/lab-architecture.svg)

## เหมาะกับใคร

System Administrator, IT Support และ Infrastructure Engineer ที่ต้องการฝึกการตั้งค่าและ Troubleshooting ของ Windows Server แบบเชื่อมโยงกันใน Project เดียว

**พื้นฐาน:** Windows Server/Windows Client, IP Address, DNS และ PowerShell ขั้นพื้นฐาน

## Skills ที่จะได้ฝึก

| Area | หัวข้อ | ผลที่คาดหวัง |
|---|---|---|
| Active Directory | Additional Domain Controller, DNS, AD Replication, FSMO | เพิ่ม DC และตรวจสถานะ Directory ได้ |
| Group Policy & Security | GPO, Windows LAPS | ใช้และตรวจสอบ Policy/Local Admin Management ได้ |
| Networking | DNS, DHCP, IP Configuration | Client ได้ Network Configuration และ Resolve Service Names ได้ |
| File Services | SMB Share, NTFS Permissions, FSRM (ตามเวลา) | Authorized Users เข้าถึง File Share ได้ถูกต้อง |
| Virtualization | Hyper-V, Virtual Switch, Checkpoint (Conditional) | เข้าใจการจัดการ VM เบื้องต้น |
| Hybrid | Azure Arc, Azure Update Manager | เห็น On-premises Server และ Update Assessment ใน Azure |
| Diagnostics | Event Viewer, Performance Monitor, PowerShell Tools | ใช้ข้อมูลจากระบบเพื่อวิเคราะห์ Incident |

[ตาราง Workshop](workshop-plan.md) · [รายละเอียด Lab](lab-briefs.md)

## Recorded Video / Pre-work (แผนเนื้อหา)

Recorded Video ปู Concepts, Features และ Demo ก่อนมา Workshop เพื่อให้วัน Onsite ลงมือทำได้ทันที

| Module | เนื้อหา |
|---|---|
| M00 | Course Overview, Lab Architecture |
| M01 | AD DS, DNS Integration และ Group Policy |
| M02 | Hybrid Management, Windows Admin Center, Azure Arc |
| M03 | Hyper-V และ Azure VMs |
| M04 | DNS, DHCP, Hybrid Networking |
| M05 | Storage, SMB, File Services, Azure File Sync |
| M06 | Windows Server Security, Windows LAPS, Security Baselines |
| M07 | Monitoring, Troubleshooting, Diagnostics |

หัวข้อขั้นสูงที่ไม่ได้ทำใน Track 1 Onsite เช่น **S2D, Storage Replica, SMB over QUIC, Hyper-V Replica และ HA** สามารถอ่านต่อใน [Track 2](advanced-track.md)

**หมายเหตุ:** รายการ Modules เป็นแผนเนื้อหาที่กำลังพัฒนา ไม่ได้หมายความว่าวิดีโอทั้งหมดเผยแพร่ครบแล้ว

## การเรียนใน Workshop

ผู้เรียนรับ Requirements ของบริษัทสมมติ แล้วทดลอง Configure ระบบเป็นลำดับ ตั้งแต่ AD DS ไปจนถึง File Server และ Azure Arc ปิดท้ายด้วยโจทย์ Troubleshooting ที่ต้องตรวจหลักฐานและยืนยันผลการแก้ไข

ผู้สอนเตรียม VM Images, Network, Accounts และส่วนที่ใช้เวลานานไว้ก่อนเพื่อให้ผู้เรียนใช้เวลาไปกับ Feature และการแก้ปัญหาจริง

## ความเกี่ยวข้องกับ AZ-802

คอร์สอิงแนวทางของ [Microsoft AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) แต่ไม่ใช่คอร์สสอบอย่างเป็นทางการของ Microsoft และการเรียน Onsite 1 วันไม่ได้ครอบคลุมทุกหัวข้อในข้อสอบ

[ค่าเรียนและ FAQ](pricing-and-faq.md)

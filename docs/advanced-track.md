# Track 2 — Advanced Infrastructure

**Hands-on Project Workshop | Windows Server 2025**

ออกแบบมาสำหรับผู้ดูแล Windows Server ที่ต้องการเข้าใจ Feature ขั้นสูง โดยเน้น **ลงมือ Configure และเห็นผลลัพธ์จริง** ไม่ใช่การติดตั้งทุกระบบตั้งแต่ศูนย์

**เวลา:** 1 วัน 09:00–17:00  
**ค่าเรียนที่เสนอ:** 5,750 บาท/Track หรือแพ็กเกจ 2 Tracks ราคาปกติ 9,900 บาท (Early Bird 8,625 บาท ตามเงื่อนไขที่ประกาศ)  
**สถานะ:** อยู่ระหว่างเตรียม Lab และทดสอบรอบเต็ม

![Track 2 — S2D Cluster](images/advanced-s2d-cluster.svg)

## Project Scenario

องค์กรกำลังสำรวจการใช้ Windows Server 2025 เพื่อทำ Storage, Virtualization และ Secure File Access ที่มีความสามารถสูงขึ้น ผู้เรียนทดลองกับ Windows Server VM Images ที่เตรียมไว้แล้วบน Hyper-V Host ใน Microsoft Azure

**Lab Goal:** สร้าง Cluster/S2D ให้พร้อมตรวจผลได้ ทดลองสร้าง Empty VM และเรียนรู้แนวทางเข้าถึง File Share ผ่าน SMB over QUIC

Workshop นี้เน้น **Feature Enablement & Verification** ไม่ได้อ้างว่าผู้เรียนได้ทดสอบความทนทานของ Production Cluster หรือติดตั้ง OS ใหม่ภายในวันเรียน

## Hands-on Topics

| Lab | ทำอะไร | ผลที่ตรวจได้ |
|---|---|---|
| A01 — Failover Cluster | ตรวจ Nodes/Network และสร้าง Cluster + Quorum Witness จาก Guest VMs ที่เตรียมไว้ | Cluster Status, Nodes, Witness |
| **A02 — Storage Spaces Direct** | Enable S2D, ตรวจ Storage Pool และทดลอง Create Virtual Disk/Volume ตามเวลา | Storage Pool / Virtual Disk ถูกสร้างและ Health อยู่ในสถานะที่คาดไว้ |
| **A03 — Nested Hyper-V** | ดู Architecture ของ Azure VM ที่เป็น Hyper-V Host, สร้าง Virtual Switch, VHDX และ Generation 2 VM เปล่า | VM ถูกสร้างใน Hyper-V Manager/PowerShell โดย **ไม่ติดตั้ง OS** |
| **A04 — SMB over QUIC** | เชื่อมต่อ SMB Share ด้วย QUIC ใน Test Network ที่เตรียม Certificate/DNS ไว้แล้ว | ตรวจสอบ Transport และ Share Access |
| A05 — Advanced Feature Showcase | สาธิต **Storage Replica หรือ Hyper-V Replica** ด้วย Environment ที่เตรียมไว้ | เห็นการทำงานและเข้าใจ Use Case/ข้อจำกัด |
| Final — Review | ตรวจผลและอธิบายว่า Feature ใดเหมาะกับ Requirement แบบใด | Checklist / Result Summary |

**หมายเหตุ:** A05 เป็น Guided Demo ไม่ใช่การติดตั้ง/Configure Replication ตั้งแต่ต้นจนจบ และเนื้อหาที่อาจเปลี่ยนตาม Lab Readiness จะยืนยันก่อนเปิดรุ่น

## Workshop Schedule (Tentative)

| เวลา | กิจกรรม |
|---|---|
| 09:00–09:20 | Requirements, Architecture & Access Lab |
| 09:20–10:00 | A01 — Failover Clustering / Witness |
| 10:00–11:10 | A02 — Enable Storage Spaces Direct |
| 11:10–12:00 | A02 — Storage Pool, Virtual Disk & Validation |
| 12:00–13:00 | Lunch |
| 13:00–13:50 | A03 — Nested Hyper-V: Create Empty VM |
| 13:50–14:40 | A04 — SMB over QUIC |
| 14:40–15:00 | Break |
| 15:00–15:45 | A05 — Storage Replica หรือ Hyper-V Replica (Guided Demo) |
| 15:45–16:25 | Troubleshooting / Review Health ของระบบที่สร้าง |
| 16:25–17:00 | Final Validation & Architecture Discussion |

ตารางนี้เป็นแผนที่ต้องผ่าน Full Dry Run ก่อนประกาศเป็นกำหนดการจริง

## WOW Features ที่จะรู้จักเพิ่มเติม

| Feature | สิ่งที่ช่วยให้ทำได้ | รูปแบบใน Track 2 |
|---|---|---|
| **S2D / ReFS / CSV** | ใช้ Storage ของหลาย Nodes และจัดการ Cluster Storage | Hands-on (การสร้าง/ตรวจสอบ) |
| **SMB over QUIC** | เชื่อม File Share ผ่าน UDP 443 โดยไม่เปิด TCP 445 ในเส้นทางทดสอบ | Hands-on เมื่อ Lab พร้อม |
| **Nested Hyper-V** | เข้าใจการทำ Hyper-V ภายใน VM และกำหนด VM Generation/Virtual Disk | Hands-on สร้าง VM เปล่า |
| **Storage Replica** | Replicate Data ระหว่าง Servers หรือ Sites | Guided Demo (เลือกหนึ่งใน A05) |
| **Hyper-V Replica** | Replicate VM สำหรับ Recovery | Guided Demo (เลือกหนึ่งใน A05) |
| **Live Migration / Hyper-V HA** | เคลื่อนย้ายหรือให้บริการ VM ผ่าน Cluster | Concept / Future Extended Workshop |
| **Hotpatch / Azure Arc** | ตรวจ Update Management Workflow และลด Reboots สำหรับ Updates ที่รองรับ | Video / Optional Demo |
| **Azure File Sync / Cloud Tiering** | ใช้ Azure Files ร่วมกับ File Server เดิม | Video / Future Extension |
| **JEA / Credential Guard / OSConfig** | เพิ่มความปลอดภัยและลดขอบเขตสิทธิ์ Administrator | Video / Future Security Extension |
| **RDMA / SMB Direct / SET** | เพิ่มประสิทธิภาพ Storage Networking | Concept / Hardware-dependent Demo |

## Prerequisites ของผู้เรียน

- ใช้งาน Windows Server, AD DS, DNS และ PowerShell ได้
- เข้าใจ Disk/Volume, NTFS/ReFS, SMB และ Virtualization Basics
- ใช้งาน Remote Console / Hyper-V Manager ตามแนวทางที่สอนได้
- มี Laptop สำหรับเข้าถึง Lab; ผู้สอนจัดเตรียม VM Images และระบบตามเงื่อนไขของคอร์ส

## Lab Architecture และข้อจำกัด

- ใช้ **Azure VM ขนาดใหญ่ที่รองรับ Nested Virtualization** เป็น Hyper-V Host และเตรียม Guest Images ไว้ก่อน
- Guest S2D Cluster ตั้งเป้า 2 Windows Server Datacenter Nodes + Witness โดยมี Virtual Data Disks อย่างน้อย 2 ลูกต่อ Node นอกเหนือจาก OS Disk
- **S2D เป้าหมายคือ Create + Verify** ไม่จำเป็นต้องทดสอบ Production Failure Scenario, Live Migration, Hyper-V HA หรือ Disaster Recovery เต็มรูปแบบ
- Azure Hyper-V Host → Prepared Guest VMs → Lab Exercises. บท Nested Hyper-V ให้สร้าง **VM เปล่า** บน Hyper-V Instance ที่ Instructor ตรวจว่าใช้งานได้; ไม่บังคับให้เปิด VM/ติดตั้ง Guest OS
- ถ้าต้องทำ Virtualization เพิ่มอีกระดับ **ภายใน Guest VM ที่ถูก Nested อยู่แล้ว** ต้องตรวจ CPU Extensions และ Hyper-V Compatibility เพิ่มเติมก่อน ไม่รับประกันการทำ Triple-Nesting
- การรัน Guest S2D Nodes บน Azure VM Host เดียวช่วยประหยัดค่าใช้จ่ายและใช้สอน Concept ได้ แต่ **ไม่ได้ให้ Host-level Fault Tolerance** และไม่ใช่ Production Deployment Model
- Microsoft ระบุว่า **Host-level Virtual Disk Snapshot/Restore ไม่รองรับ** สำหรับ S2D Guest Cluster; ผู้สอนต้องทดสอบการ Reset/Rebuild และ Backup Strategy ที่เหมาะสม
- ก่อนเปิดรุ่นต้องยืนยัน Azure VM Size, CPU/RAM/Disk IOPS, Host Security Type = Standard, Outbound/Guest Networking, Windows Licensing และ VM Capacity ของจำนวนผู้เรียนจริง

### Microsoft Learn References

- [Storage Spaces Direct: Deployment](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/deploy-storage-spaces-direct)
- [Storage Spaces Direct in Guest VMs](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-spaces-direct-in-vm)
- [Nested Virtualization](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization)
- [SMB over QUIC](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-over-quic)

> **Track 2 is an evaluation/training lab.** ไม่ใช่ Hardware-certified หรือ Production HA Architecture Reference

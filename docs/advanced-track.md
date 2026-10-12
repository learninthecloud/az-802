# Track 2 — Advanced & Hybrid

**Windows Server 2025 | AZ-802 Hands-on Project Workshop**  
**Duration:** 1 วัน 09:00–17:00  
**ราคาเสนอ:** 5,750 บาท (2 Tracks ปกติ 9,900 บาท; Early Bird 8,625 บาท ตามเงื่อนไขที่ประกาศ)

![Track 2 — Full Hybrid Lab Architecture](images/advanced-track-architecture.svg)

## เป้าหมาย

ทำงานกับ Advanced Windows Server และ Azure Hybrid Services โดยใช้ Guest Images และ Cloud Prerequisites ที่เตรียมไว้แล้ว เพื่อให้ได้ทดลอง Feature สำคัญภายในหนึ่งวัน

**Track 2 ครอบคลุม Objectives 06–08, 11, 13 และ 15** ตาม [Selected AZ-802 Lab Catalog](lab-catalog.md) ไม่ได้เพิ่ม SMB over QUIC, Live Migration หรือ Storage Replica เป็นหัวข้อหลักแทนรายการที่เลือกไว้

## Selected Lab Activities

| Objective | Hands-on / Guided Activities | แนวทาง |
|---:|---|---|
| 06 — Azure Hybrid Management | Implement Azure Arc; Azure Update Manager | Guided |
| 07 — Hyper-V | Install/Configure Hyper-V; Enable Nested Virtualization; Create Empty VM | Guided / Hands-on |
| 08 — Azure Compute | Create Azure VM; Create VM Scale Set | Guided / Hands-on |
| 11 — Azure Files | Create Azure File Share; Azure File Sync | Guided |
| 13 — Windows Server Storage | Implement Storage Spaces Direct (S2D) | Guided: Create + Verify |
| 15 — Secure AD DS / Hybrid Identity | Entra Connect Sync; Entra Password Protection for AD DS; AD Hardening; AD Delegation | Guided |

**Scope Note:** Entra Connect Sync เป็น Hybrid Identity Feature ที่ใส่เพื่อให้ได้ใช้จริงร่วมกับ Azure แม้จะไม่ใช่ Bullet โดยตรงของ AZ-802 Secure AD DS Skill Objective

## Lab Architecture

ภาพแสดง **Logical Roles** ไม่ใช่จำนวน Azure VMs ที่ต้องเปิดจริงทั้งหมด

- **DC01:** AD DS, DNS, Entra Password Protection DC Agent, AD Hardening/Delegation
- **SYNC01:** Entra Connect Sync, Entra Password Protection Proxy (แยก Logical Role จาก DC)
- **FS01:** SMB/File Server, Azure File Sync Agent และ File Share Witness สำหรับ Lab Cluster
- **S2D01 + S2D02:** Two-node S2D Evaluation Cluster (แยก Guest Nodes) พร้อม Virtual Data Disks
- **CLIENT01:** ตรวจการเข้าถึง, DNS, Identity และ File Services
- **HV-AZ01:** Azure VM ที่รองรับ Nested Hyper-V และเป็น Host สำหรับ Prepared Guest VMs
- **Azure Services:** Microsoft Entra ID, Azure Arc/Update Manager, Azure Files, Azure VM/VM Scale Set

บาง Roles รวมเป็น VM เดียวกันได้ใน Lab เพื่อประหยัดทรัพยากร แต่ต้องไม่ย้าย Witness เข้าไปบน S2D Node และต้องแยก Data/OS Disks ของ S2D ให้ถูกต้อง

[ดูรายละเอียด Logical Roles และตัวเลือกการรวม VM](lab-topology.md)

### S2D Cluster Dependencies

![S2D Cluster Dependency Model](images/advanced-s2d-cluster.svg)

สำหรับ Track 2 เป้าหมายคือ **Enable S2D / Create Storage Pool หรือ Virtual Disk / Verify Health** ไม่ใช่ทดลอง Production HA, Live Migration หรือ Cluster Failover เต็มรูปแบบ

## Workshop Schedule (Tentative)

| เวลา | Lab Session | Objective |
|---|---|---|
| 09:00–09:20 | Scenario, Architecture, Lab Access | Intro |
| 09:20–10:10 | A01 — Azure VM and VM Scale Set | 08 |
| 10:10–11:00 | A02 — Hyper-V, Nested Virtualization, Empty VM | 07 |
| 11:00–12:00 | A03 — S2D Enable, Storage Pool / Virtual Disk, Verify | 13 |
| 12:00–13:00 | Lunch | — |
| 13:00–13:50 | A04 — Azure Arc and Azure Update Manager | 06 |
| 13:50–14:40 | A05 — Azure File Share and File Sync | 11 |
| 14:40–15:00 | Break | — |
| 15:00–16:15 | A06 — Entra Connect Sync, Password Protection, AD Security/Delegation | 15 |
| 16:15–17:00 | Validation and Troubleshooting Review | All |

**รวม:** 480 นาที (พัก 80 นาที, เรียน/ปฏิบัติ 400 นาที) ต้อง Full Dry Run ก่อนยืนยันตาราง

> **ข้อจำกัดเวลา:** 6 Objectives นี้มีหลาย Activities ที่ใช้ Provisioning/Sync นาน จึงเตรียม Azure Resources, AD DS, Windows Server Images, S2D Data Disks, Identity Prerequisites และ Pre-installed Services ล่วงหน้า แล้วให้ผู้เรียนทำขั้นตอนที่สำคัญ พร้อมตรวจผลจริง

## Lab Outcomes

### A01 — Azure VM / VM Scale Set
- Create Azure VM และ Create VMSS ด้วย Resource Group/Network/Quota ที่เตรียมไว้
- Verify Provisioning State และ Scale Set Instance Configuration; อาจใช้ Small Demo VM/VMSS เพื่อควบคุมค่าใช้จ่าย

### A02 — Hyper-V / Nested Virtualization
- ใช้ Azure VM ขนาดใหญ่ที่รองรับ Nested Hyper-V
- ตรวจ Hyper-V Role, Virtual Switch, VHDX, VM Configuration
- **นักเรียนสร้าง VM เปล่า ไม่ต้องติดตั้ง OS หรือ Boot Guest**
- ไม่รับประกันการทำ Triple-Nesting ถ้าทำ Hyper-V เพิ่มใน Guest ที่เป็น Nested VM อยู่แล้ว; จัด Exercise บน Host/Guest ที่ผ่าน Compatibility Test

### A03 — Storage Spaces Direct
- Guest Nodes S2D01/S2D02 เป็น Windows Server Datacenter, มี Witness ภายนอก Cluster Nodes
- เตรียม Guest VM Images, Cluster Prerequisites และ Virtual Data Disks ล่วงหน้า
- ให้นักเรียน Enable/Create S2D Storage Pool, Create Virtual Disk/Volume ตามเวลาที่มี และ Verify Health
- ไม่ทดสอบ Production Performance/Hardware Failure หรือใช้ Host-level Snapshot เป็น Recovery Strategy ของ S2D Guest Cluster

### A04 — Azure Arc / Update Manager
- ใช้ Nested Guest Server ที่ไม่ใช่ Native Azure VM Resource เป็น Arc-enabled Server
- Onboard/Verify Connection และ Check for Updates/Assessment โดยไม่บังคับ Patch Install หรือ Reboot

### A05 — Azure Files / File Sync
- เตรียม Storage Account, Sync Service และ Server Registration Prerequisites
- สร้าง Azure File Share และตรวจ Sync Group/Endpoint, File Sync Status ตามเวลา
- FS01 เป็น File Server Role ที่มี Azure File Sync Agent

### A06 — Hybrid Identity / Secure AD DS
- DC01 มี AD DS/DNS และเตรียมให้ใช้ Entra Password Protection DC Agent
- SYNC01 เป็น Domain-joined Member Server สำหรับ Entra Connect Sync และ Password Protection Proxy
- ฝึก Hybrid Identity Sync กับ Tenant/Verified Domain ที่เตรียมไว้ก่อน; ตรวจ Sync Status และ Object ตามเป้าหมาย
- Entra Password Protection: เริ่มจาก Audit Mode และตรวจ Proxy/DC Agent Status
- AD Hardening: กำหนด Controls ที่ปลอดภัยต่อ Lab; AD Delegation: มอบสิทธิ์ใน OU เป้าหมายให้ Account ทดสอบ
- ไม่ใช่การทำ Entra Connect Production Migration/Configuration ตั้งแต่ต้นจนจบ

## ข้อจำกัดของ Lab

- Logical Roles ไม่จำเป็นต้องเท่ากับ Physical VMs แต่แสดงเพื่อให้เข้าใจ Dependency
- S2D ที่ทดสอบบน Guest Nodes ซึ่งอยู่ใน Physical/Azure Host เดียวกัน **ไม่ได้รับประกันความทนทานต่อ Host Failure**
- Two-node S2D Guest Cluster ต้องมี Witness และ Virtual Data Disks อย่างน้อยสองลูกต่อ Guest (ไม่รวม OS Disk)
- การ Sync/Replication/Agent Onboarding อาจใช้เวลาไม่แน่นอน จึงมี Prepared Stages เพื่อรักษาเวลาเรียน
- Version, Windows Licensing, Azure Quota, VM Sizing และ Nested Virtualization Compatibility ต้องตรวจใน Dry Run จริง
- เนื้อหานี้เป็น Training/Evaluation Lab ไม่ใช่ Production Reference Design

## Microsoft References

- [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802)
- [S2D Guest VMs](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-spaces-direct-in-vm)
- [Nested Virtualization](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization)
- [Azure Arc](https://learn.microsoft.com/en-us/azure/azure-arc/servers/overview)
- [Azure File Sync](https://learn.microsoft.com/en-us/azure/storage/file-sync/file-sync-planning)
- [Entra Connect Prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-prerequisites)

[Track 1](course-outline.md) · [Full 18-Objective Catalog](lab-catalog.md) · [Pricing & FAQ](pricing-and-faq.md)

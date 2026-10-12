# Lab Topology and Logical Roles

Workshop ใช้ **Logical Architecture** เพื่อสอนความสัมพันธ์ของ Services และ Dependencies ไม่ได้หมายถึงต้องมี Physical Server หรือ Azure VM แยกสำหรับทุก Role

## Track 1 — Administration

![Track 1 Logical Architecture](images/lab-architecture.svg)

| Logical VM | Main Roles / Activities |
|---|---|
| DC01 | First DC, DNS, FSMO, AD Recycle Bin, AD principals |
| DC02 | Additional DC, DNS, AD Sites/Replication |
| FS01 | SMB File Share, FSRM, DHCP Server 1 |
| FS02 | DFS Namespace/Targets, DHCP Server 2 (Failover Partner) |
| MGMT01 | Windows Admin Center, Management/Monitoring |
| CLIENT01 | Domain Join, GPO/SMB Access, Basic Diagnostics |

ตัวอย่างการรวม Roles ใน Lab: **MGMT01 กับ FS02** (ต้องทดสอบ Role Compatibility ก่อน), ใช้ DC01/DC02 แยกสำหรับ AD Replication และ FS01/FS02 แยก DHCP Partner เพื่อให้มีสอง DHCP Servers จริง

การรวม WAC/Management กับ File Server เป็นแนวทางประหยัด VM เฉพาะ Lab ไม่ใช่คำแนะนำด้าน Security สำหรับ Production

## Track 2 — Advanced & Hybrid

![Track 2 Complete Logical Architecture](images/advanced-track-architecture.svg)

| Logical VM / Resource | Main Roles / Activities |
|---|---|
| HV-AZ01 (Azure VM) | Hyper-V Host ที่รองรับ Nested Virtualization; เตรียม Guest Images |
| DC01 (Nested Guest) | AD DS/DNS; Entra Password Protection DC Agent; AD Hardening/Delegation |
| SYNC01 (Nested Guest) | Entra Connect Sync; Entra Password Protection Proxy |
| FS01 (Nested Guest) | SMB/File Server; Azure File Sync Agent; File Share Witness |
| S2D01 + S2D02 (Nested Guests) | S2D/Failover Cluster Nodes; 2+ Data Disks/Node |
| CLIENT01 (Nested Guest) | Identity/File Access Validation |
| Empty VM (Created in Lab) | VM Definition/Virtual Disk/Network only; no Guest OS installed |
| Microsoft Entra ID (Azure Service) | Hybrid Identity Target |
| Azure Arc + Update Manager | Management and Update Assessment for supported Guest |
| Azure Files / Storage Account | Azure File Share + File Sync |
| Azure VM / VM Scale Set | Native Azure Compute Lab (separate from Guest VM definitions) |

### Dependencies

- **Domain:** S2D Nodes, FS01 และ SYNC01 ใช้ DC01/DNS ตาม Lab Setup
- **Quorum:** File Share Witness อยู่บน **FS01 นอก S2D Cluster Nodes**
- **Hybrid Identity:** Entra Connect Sync รันบน SYNC01 ไม่ใช่ DC01; Password Protection Proxy บน SYNC01 และ DC Agent บน DC01
- **File Sync:** FS01 ↔ Azure Files ผ่าน Storage Sync Service/Registered Agent
- **Azure Arc:** Server Guest ถูก Onboard ให้แสดงเป็น Arc-enabled Resource ไม่ใช่ Native Azure VM Resource
- **Azure VM/VMSS:** เป็น Azure Compute Resources แยกจาก Empty VM ที่สร้างภายใน Hyper-V
- **S2D:** Cluster Nodes ต้องเป็นคนละ VM และมี Virtual Data Disks เหมาะสม; ไม่วาง Witness บน S2D01/S2D02

![S2D Dependencies](images/advanced-s2d-cluster.svg)

### Physical/Nested Deployment for Classroom

```text
Microsoft Azure
  HV-AZ01  (large Azure VM; Hyper-V Host)
    DC01       AD DS / DNS / Password Protection DC Agent
    SYNC01     Entra Connect Sync / PP Proxy
    FS01       File Share / File Sync / Witness
    S2D01      S2D Node 1 / Data Disks
    S2D02      S2D Node 2 / Data Disks
    CLIENT01   Optional / validation
    EMPTY-VM   Created by students; no OS installed

Azure-native resources (outside nested Guest VMs)
  Microsoft Entra ID
  Azure Arc / Azure Update Manager
  Azure Storage / Azure Files
  Azure VM / Virtual Machine Scale Set
```

Guest VMs อาจถูก Consolidate ตาม Resource Limits เช่นรวม Test Client หรือ Management Functions เข้ากับ Member Server แต่ต้องตรวจ Compatibility และผลกระทบต่อ Lab Objectives ก่อนเสมอ

**หลักการ:** Diagram แสดง Roles ให้ครบ ส่วนรายการ VM ที่ใช้งานจริงจะยืนยันหลัง Full Dry Run และอาจแตกต่างจาก Logical Architecture

## Reference

- [Track 1](course-outline.md)
- [Track 2](advanced-track.md)
- [Full Selected Lab Catalog](lab-catalog.md)

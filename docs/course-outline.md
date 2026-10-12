# Track 1 — Administration: Course Outline (AZ-802)

หลักสูตรนี้เป็น **Hands-on Track 1**; ดู [Track 2 — Advanced Infrastructure](advanced-track.md) สำหรับ S2D, Failover Cluster, High Availability และ SMB over QUIC

## ภาพรวม

**รูปแบบ:** Recorded Video (เรียนล่วงหน้า) + Onsite Hands-on Workshop 1 วัน (09:00–17:00)  
**Lab Platform:** Windows Server 2025, Windows 11 และ Microsoft Azure  
**แนวทาง:** เริ่มจาก Requirements แล้วลงมือ Configure, Validate และ Troubleshoot

คอร์สนี้อ้างอิงขอบเขตของ [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) ซึ่งมีชื่อสอบว่า **Administering Windows Server** ไม่ได้จำกัดเฉพาะ Windows Server 2025 แต่เราเลือก Windows Server 2025 เป็นระบบหลักในการสอน

**หมายเหตุ:** เอกสารนี้เป็นแผนพัฒนาคอร์ส ไม่ได้หมายความว่าวิดีโอหรือ Lab ทั้งหมดผลิตเสร็จแล้ว และ Workshop 1 วันไม่ได้ครอบคลุมทุกหัวข้อในข้อสอบ

![AZ-802 Project Lab Architecture](images/lab-architecture.svg)

*ภาพรวม Environment สำหรับ Onsite Workshop — เป็น Conceptual Diagram ไม่ใช่ Screenshot จาก Windows Server*

## ผู้เรียนที่เหมาะสม

- System Administrator / Infrastructure Engineer ที่ดูแล Windows Server, AD DS, DNS หรือ File Server
- IT Support ที่ต้องการขยับไปทำงาน Server Administration
- ผู้ที่เริ่มดูแล Windows Server ร่วมกับ Azure และต้องการฝึกจากโจทย์งานจริง

**พื้นฐานที่ควรมี:** Windows Server/Windows Client, IP Address/Subnet, DNS เบื้องต้น และใช้งาน PowerShell ขั้นพื้นฐานได้

## สิ่งที่ผู้เรียนควรทำได้หลังจบ

1. เพิ่ม Domain Controller และตรวจสอบ AD Replication, DNS และ FSMO
2. จัดการ Group Policy และ Windows LAPS พร้อมตรวจสอบการใช้งานจริง
3. ตั้งค่า DNS/DHCP และวิเคราะห์ปัญหา Name Resolution กับ IP Configuration
4. ออกแบบสิทธิ์เข้าถึง File Share ด้วย SMB, Share Permissions และ NTFS Permissions
5. เชื่อมต่อ Windows Server กับ Azure Arc และตรวจสอบสถานะ Windows Updates
6. ใช้ Event Viewer, Performance Monitor และคำสั่ง Diagnostic เพื่อหาสาเหตุของปัญหา

## Recorded Video — โครงสร้างเนื้อหา

วิดีโอเน้น Concept, Decision และ Demo เพื่อให้ Onsite ไม่ต้องใช้เวลาปูพื้นฐานซ้ำ เวลาข้างล่างเป็น **เป้าหมายการผลิตเบื้องต้น** ไม่ใช่ความยาววิดีโอที่บันทึกเสร็จแล้ว

| Module | เนื้อหา | เวลาเป้าหมาย |
|---|---|---:|
| M00 | Course Overview, Lab Architecture และวิธีเรียน | 20 นาที |
| M01 | AD DS และ Group Policy | 90 นาที |
| M02 | Windows Server Hybrid Management | 60 นาที |
| M03 | Hyper-V และ Azure VMs | 60 นาที |
| M04 | DNS, DHCP และ Hybrid Networking | 60 นาที |
| M05 | Storage, SMB และ File Services | 90 นาที |
| M06 | Windows Server และ AD DS Security | 75 นาที |
| M07 | Monitoring และ Troubleshooting | 75 นาที |

### M01 — Active Directory Domain Services

- Domain/Forest, DC, DNS Integration และ Sites
- Domain Controller Deployment, FSMO และ AD Replication
- Users, Groups และ Service Accounts
- Group Policy และ Group Policy Preferences
- **Overview:** RODC, Multi-domain/Forest และ Trust Relationships

### M02 — Hybrid Windows Server Management

- Windows Admin Center และ PowerShell Remoting
- Remote Management: RDP, SSH และ JEA (แนะนำแนวคิดและกรณีใช้งาน)
- Azure Arc: Connected Machine Agent, Resource และ Extensions
- Azure Update Manager: Assessment, Scheduling และ Maintenance
- **Overview:** Azure Automation Runbooks

### M03 — Virtual Machines

- Hyper-V: Virtual Switch, VHDX, VM Settings, Checkpoints และ Replica
- Availability และการจัดการ Hyper-V VMs
- Azure VMs: Storage, Size, Networking และ Availability
- **Overview:** Azure Bastion, JIT Access, Scale Sets และ GPU Partitioning

### M04 — Networking

- AD-integrated DNS, Zones, Records, Forwarders และ Conditional Forwarders
- DNS Troubleshooting และ Hybrid Name Resolution
- DHCP: Scope, Options, Reservation และ Failover
- **Overview:** DNS Policies และ DNSSEC

### M05 — Storage and File Services

- Disks, Volumes, NTFS/ReFS และ Storage Spaces
- SMB Share, Share/NTFS Permissions และ Effective Access
- FSRM, DFS Namespace/Replication
- Azure Files และ Azure File Sync
- **Overview:** Storage Replica, Data Deduplication, S2D, iSCSI, SMB over QUIC และ SMB Direct

### M06 — Windows Server Security

- Group Policy Security Settings, Windows Firewall และ Windows LAPS
- AD DS Security: Privileged Groups, Delegation, Protected Users และ Password Policies
- Security Baseline/OSConfig และ Defender for Servers
- **Overview:** Credential Guard, Application Control และ Microsoft Entra Password Protection for AD DS

### M07 — Monitoring and Troubleshooting

- Event Viewer, Performance Monitor และ Data Collector Sets
- Windows Admin Center Monitoring
- Azure Monitor, Azure Monitor Agent, DCR และ Alerts
- เครื่องมือ: dcdiag, repadmin, gpresult, Resolve-DnsName, Test-NetConnection
- Troubleshooting: Replication, DNS, Connectivity, Kerberos, Secure Channel, Update และ Storage
- **Overview:** AD Recycle Bin, DSRM และ SYSVOL Recovery

## Onsite Workshop — สิ่งที่ลงมือทำ

Workshop ใช้ Infrastructure เดียวกันตลอดวัน แบ่งหัวข้อดังนี้

| Lab | หัวข้อ | ความสำคัญ |
|---|---|---|
| 01 | เพิ่ม DC และตรวจสอบ AD Replication | Must do |
| 02 | GPO และ Windows LAPS | Must do |
| 03 | DNS และ DHCP | Must do |
| 04 | SMB/NTFS Permissions และ FSRM | Must do |
| 05 | Hyper-V Virtual Switch และ Checkpoint | Should do — ตามความพร้อม Lab |
| 06 | Azure Arc และ Update Manager | Must do |
| 07 | Monitoring และ Diagnostic Tools | Must do |
| Final | Troubleshooting Incident | Must do |

รายละเอียดเวลาอยู่ใน [Workshop Plan](workshop-plan.md) และขั้นตอน/ผลลัพธ์ของแต่ละ Lab อยู่ใน [Lab Briefs](lab-briefs.md)

## สิ่งที่ไม่ได้ทำ Onsite แต่ควรอยู่ในวิดีโอ

RODC, Cross-Forest Trust, Hyper-V Replica/Cluster, Storage Spaces Direct, Storage Replica, SMB over QUIC, DFS Migration, Azure VM High Availability, JEA ขั้นสูง และ AD Recovery แบบเต็มรูปแบบ

การไม่ทำ Onsite ไม่ได้หมายความว่าหัวข้อเหล่านี้ไม่สำคัญต่อข้อสอบ แต่ใช้เวลามากเกินกว่าจะฝึกจนจบใน Workshop 1 วัน

## ความสัมพันธ์กับหัวข้อ AZ-802

| Skills measured (Microsoft) | Exam weight | Recorded Video | Onsite |
|---|---:|---|---|
| Deploy and manage AD DS | 20–25% | M01 | Lab 01–02 |
| Manage Windows Server in hybrid environment | 10–15% | M02 | Lab 06 |
| Manage virtual machines | 10–15% | M03 | Lab 05 (Optional) |
| Implement on-premises/hybrid networking | 10–15% | M04 | Lab 03 |
| Manage storage and file services | 15–20% | M05 | Lab 04 |
| Secure Windows Server infrastructure | 10–15% | M06 | Lab 02, 04 |
| Monitor and troubleshoot Windows Server | 15–20% | M07 | Lab 07, Final |

ตัวเลขเป็นน้ำหนักข้อสอบตาม Study Guide ไม่ใช่สัดส่วนเวลาสอน และยังต้องตรวจสอบ Study Guide ใหม่ก่อนเปิดรุ่นทุกครั้ง

## รูปแบบการประเมิน

- **ก่อน Onsite:** ดูวิดีโอและทำ Pre-work Check เพื่อยืนยันว่า Login Lab และใช้เครื่องมือพื้นฐานได้
- **ระหว่าง Lab:** ทำงานตาม Requirements และใช้ Verification Commands ตรวจผล
- **Final Challenge:** แก้ Incident ที่เตรียมไว้ พร้อมอธิบายหลักฐานที่ใช้ตัดสินใจ

## ข้อมูลสำหรับวางแผนรุ่นแรก (ยังไม่ประกาศ)

- ผู้เรียนเป้าหมาย: 20–25 คน
- รูปแบบห้อง: แนะนำทำงานเป็นคู่ 1 Lab Pod ต่อ 2 คน (หรือ Pod ส่วนตัวหาก Infrastructure เพียงพอ)
- ราคาเสนอเบื้องต้น: 5,750 บาท/คน รวม Recorded Video + Onsite Workshop; ต้องยืนยันก่อนเปิดขาย
- ผู้สอนและทีมงานต้องเตรียม Environment, บัญชี Azure, สิทธิ์ใช้งาน และขั้นตอน Reset Pod ล่วงหน้า

**เอกสารอ้างอิง:** [Microsoft Learn — AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) (Last updated: 6 July 2026)

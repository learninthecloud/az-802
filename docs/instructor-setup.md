# Instructor Setup — Lab Environment and Delivery Checklist

เอกสารสำหรับเตรียม Onsite Workshop จำนวนประมาณ 20–25 คน ไม่ใช่ขั้นตอนติดตั้ง Production

![AZ-802 Lab Architecture](images/lab-architecture.svg)

## ข้อเสนอด้าน Delivery

- **แนะนำ:** ทำงานเป็นคู่ Pod ละ 2 คน = ประมาณ 10–13 Pods
- ถ้าต้องการคนละ Pod ต้องเพิ่ม Compute, Windows Licensing, Network Segments, Azure Resources และคนดูแล Lab ตามสัดส่วน
- เตรียม Instructor Pod และ Standby Pod อีกอย่างน้อย 1 ชุดสำหรับ Demo/กู้ปัญหา
- วาง Assistant Instructor อย่างน้อย 1 คนสำหรับช่วยตรวจเครื่อง/แก้ปัญหาเฉพาะ Pod

## Baseline ต่อ Pod

| VM | OS | สถานะก่อนเริ่ม | หน้าที่ |
|---|---|---|---|
| DC01 | Windows Server 2025 | สร้าง Domain ไว้แล้ว; DNS/AD DS Healthy | Existing DC |
| DC02 | Windows Server 2025 | Join Domain, IP/DNS ถูกต้อง; พร้อม Promote | Additional DC |
| FS01 | Windows Server 2025 | Join Domain, มี Data Disk; Role/Feature พร้อม Configure | SMB/FSRM และ DHCP สำหรับ Lab |
| CLIENT01 | Windows 11 | Join Domain, เข้า Lab ได้; เริ่มด้วย IP ที่ใช้งานได้ | GPO/SMB/DHCP Test |
| HV01 (Optional) | Supported Hyper-V Host | มี Test VM; Nested Virtualization ตรวจแล้ว | Hyper-V Lab |

> ขนาด CPU/RAM/Disk ต้องผ่าน Full Dry Run ก่อนใช้งานจริง อย่าใช้ Minimum OS Requirement เป็น Capacity Plan ของห้องเรียน

### Network และ Identity

- แยก Layer-2/DHCP Broadcast Domain ของแต่ละ Pod และแยกจาก Production
- DNS ของ Domain ชี้มาที่ DC01/DC02 ตามสถานะของ Lab
- เตรียม DHCP Scope Range, Gateway, DNS Server Options และ Reservation Details ต่อ Pod
- Prepare External/Test DNS Zone สำหรับ Conditional Forwarder ถ้าจะให้ทำหัวข้อนี้จริง; ถ้าไม่มีให้สอน DNS Forwarding พื้นฐานแทน
- มี Lab Admin Account และ Standard User Accounts อย่างน้อย 2 คนต่อ Pod
- เตรียม Groups และ Folder Access Matrix (ใครอ่าน/เขียนอะไรได้) สำหรับ Lab 04
- Credentials ต้องเก็บในระบบแจกบัญชีที่เหมาะสม **ห้าม Commit Password/Token ลง Repository**

### Windows LAPS

ก่อนวันเรียนต้องตรวจ:
- [ ] AD DS Schema รองรับ Windows LAPS และได้ทำ `Update-LapsADSchema` แล้ว
- [ ] OU ที่ใช้มี Permission ให้ Computer Account เขียน LAPS Data ได้
- [ ] ตั้ง Permission สำหรับผู้ตรวจสอบ Password/Decrypt อย่างจำกัด
- [ ] Policy Template และ Local Admin Account ที่จะบริหารจัดการพร้อม
- [ ] ทดสอบ Backup ไป AD DS และ Event Log บนหนึ่งเครื่องจริง
- [ ] ไม่ใช้ Real Password/Plaintext Password เป็นหลักฐาน Screenshot

Reference: [Windows LAPS — Microsoft Learn](https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-scenarios-windows-server-active-directory)

### Azure Arc และ Update Manager

- [ ] มี Subscription/Resource Group และ RBAC สำหรับ Pod ทุกชุด
- [ ] ตรวจ Resource Provider Registration ตาม Requirement ของ Azure Services
- [ ] มี Internet Egress/Proxy/DNS ที่ทำให้ Azure Connected Machine Agent ต่อ Service ได้
- [ ] เลือก Onboarding Method ที่จะใช้เหมือนกันทุก Pod และ Smoke Test แล้ว
- [ ] ตั้ง Naming Convention: `rg-az802-podXX`, ชื่อ Arc Resource ไม่ชนกัน
- [ ] ตรวจวิธีเปิด Update Assessment และเตรียมผล Scan ตัวอย่าง
- [ ] ตรวจการคิดค่าใช้จ่ายและตั้ง Budget/Quota ที่เหมาะสมกับ Lab
- [ ] มี Azure Arc Server สำหรับ Instructor ที่ Connected อยู่แล้ว หาก Pod ใดติดปัญหา

การสแกน Updates และการติดตั้ง Agent/Extension อาจใช้เวลาต่างกันตาม Network/Service จึงไม่ควรใช้การรอ Scan หรือการติดตั้ง Patch จริงเป็นเกณฑ์วัดความสำเร็จในช่วง 45 นาที

References: [Arc Setup](https://learn.microsoft.com/en-us/azure/azure-arc/servers/onboard-windows-server), [Update Assessment](https://learn.microsoft.com/en-us/azure/update-manager/assessment-options)

### Hyper-V (Conditional)

- [ ] Host รองรับ Hyper-V และ Nested Virtualization หากใช้ VM ซ้อน VM
- [ ] มี Virtual Switch และ Test VM ที่สามารถ Restore ได้
- [ ] Checkpoint เฉพาะ Test VM ไม่ให้ผู้เรียน Apply Checkpoint บน DC
- [ ] ทดลองภาระ CPU/RAM พร้อมกันทุก Pod
- [ ] เตรียมทางเลือกหาก Nested Virtualization ใช้งานไม่ได้

Reference: [Nested Virtualization — Microsoft Learn](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization)

## Checkpoints สำหรับ Instructor

### T-7 วัน

- [ ] ยืนยัน Version/Edition ของ Windows Server และ Windows 11
- [ ] ยืนยัน Windows/Hypervisor Licensing และ Azure Subscription
- [ ] ทดลองทำทุก Lab ให้จบด้วย Environment จริงที่ใช้สอน
- [ ] วัดเวลาจริงต่อ Lab และปรับตามจำนวนผู้เรียน
- [ ] ทบทวน MS Learn AZ-802 Study Guide ฉบับล่าสุด

### T-1 วัน

- [ ] Clone/Create ทุก Pod พร้อม Network Segmentation
- [ ] ตรวจ DC01 Health และ Domain Join ของ DC02/FS01/CLIENT01
- [ ] ทดสอบ Local Admin, Domain Admin และ Standard User Access
- [ ] ทดสอบ Windows LAPS End-to-End
- [ ] ทดสอบ Azure Arc Connection และ Check for Updates
- [ ] ทดสอบ Hyper-V Option หรือประกาศใช้ Alternate Exercise
- [ ] สร้าง Snapshot/Baseline สำหรับ Reset Pod และ Verify Restoration
- [ ] เปิดเครื่อง/ทดสอบ Remote Console จาก Network ห้องเรียนจริง

### ก่อน 09:00

- [ ] Confirm Lab Portal/Remote Access ทุก Pod
- [ ] Confirm DNS/Internet/Egress ไป Azure
- [ ] Confirm FS01 Data Volume พร้อมสำหรับ Lab 04
- [ ] Prepare Incident Fault Cases แยกไฟล์จาก Student Material
- [ ] มี Instructor Demo Pod และ Troubleshooting Matrix

## Failure and Reset Plan

| ปัญหา | วิธีรับมือ |
|---|---|
| DC02 Promote ไม่ผ่าน | ให้ตรวจ DNS และ Connectivity ก่อน; ถ้ายังไม่ผ่านให้ใช้ Pod สำรองเพื่อ Demo แล้วแก้เป็นช่วง Debrief |
| DHCP ทำให้ Client หลุด | ต่อ Console หรือคืน IP Static ชั่วคราว จากนั้นตรวจ Scope/Options และ Network Segment |
| Windows LAPS ไม่ Backup | ตรวจ GPO Scope, AD Permission และ LAPS Operational Event Logs |
| SMB Share เข้าไม่ได้ | ตรวจ DNS → Connectivity → Share Permissions → NTFS Permissions ด้วย User Test |
| Azure Arc Onboarding ช้า | ให้ทำ Local Diagnostics และใช้ Connected Instructor Server ต่อ Update Manager |
| Hyper-V ไม่พร้อม | แปลงช่วงเวลาเป็น Extended File Services หรือ Azure Files/File Sync Demo |
| Final Fault ทำให้ Pod ใช้งานไม่ได้ | Restore Baseline ของ Pod ทั้งชุดหรือใช้ Fault Rollback ที่ทดสอบแล้ว |

**AD DS Restore:** การ Restore DC แยกเครื่องด้วย VM Checkpoint มีความเสี่ยงและต้องเข้าใจพฤติกรรมของ AD DS/VM-GenerationID; ออกแบบ Reset Plan ของทั้ง Pod ให้ผ่านการทดสอบก่อน และไม่ใช้แนวทางนี้กับ DC ใน Production

## สิ่งที่ยังต้องทำก่อนจำหน่ายคอร์ส

- [ ] Provisioning Script และ Environment Template
- [ ] Student Guide และ Instructor Answer Key
- [ ] ตาราง Required/Optional Access Rights
- [ ] Final Incident Scripts + Tested Rollback
- [ ] รายการ Azure Resources ที่ใช้จริงและ Cost Estimate
- [ ] Full Dry Run แบบจับเวลา รวม Reboots, Agent Onboarding และ Q&A

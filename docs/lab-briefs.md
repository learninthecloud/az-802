# Lab Briefs — Windows Server 2025 (AZ-802)

เอกสารนี้เป็น **โจทย์และเกณฑ์ตรวจผล (Lab Specification)** สำหรับทำ Student Guide และ Instructor Guide ต่อ ไม่ใช่ Step-by-step Manual ฉบับสมบูรณ์

ทุก Lab ให้เริ่มด้วย Requirements, ลงมือทำ, ตรวจผล แล้วค่อยสรุปสิ่งที่ผิดพลาดได้จริง

## ข้อมูลร่วมกัน

**Domain:** corp.example.test  
**Machines:** DC01, DC02, FS01, CLIENT01 (Windows 11)  
**Optional:** HV01 และ VM สำหรับทดลอง Hyper-V  
**Groups ตัวอย่าง:** GG-File-Finance-RW, GG-File-HR-RO  
**Share:** `\\FS01\Departments`  
**เงื่อนไข:** ใช้ Network และบัญชี Lab ที่แยกจาก Production เท่านั้น

---

## Lab 01 — Deploy an Additional Domain Controller (50 นาที)

![AD DS replication from DC01 to DC02](images/lab-01-ad-ds.svg)

**Requirement:** เพิ่ม DC เพื่อให้ Domain ไม่พึ่ง DC01 เครื่องเดียว และยืนยันว่า AD DS Replication ทำงานถูกต้อง

**สิ่งที่ทำ**
1. ตรวจ DNS/IP ของ DC02 และยืนยันว่าเครื่อง Join Domain แล้ว
2. Promote DC02 เป็น Additional Domain Controller
3. ตรวจ DNS Registration และ SYSVOL/NETLOGON Shares
4. ตรวจ AD Replication และ FSMO Role Placement

**Validation / Evidence**
- `dcdiag` ไม่มี Error สำคัญเกี่ยวกับ Health ของ DC ที่เพิ่งเพิ่ม
- `repadmin /replsummary` และ `repadmin /showrepl` แสดง Replication สำเร็จ
- `netdom query fsmo` ระบุ FSMO Role Owners ได้
- จาก Client สามารถ Resolve ชื่อ DC01 และ DC02 ได้

**Instructor Notes:** ติดตั้ง AD DS Role/เตรียม Domain Join ไว้ได้ แต่ต้องเหลือขั้นตอน Promote ให้ผู้เรียนทำ และเผื่อเวลารอ Restart

**Stretch:** ตรวจ Site/Subnet หรือย้าย FSMO ชั่วคราว (ทำเฉพาะ Instructor Demo)

---

## Lab 02 — Group Policy and Windows LAPS (45 นาที)

![Group Policy and Windows LAPS](images/lab-02-gpo-laps.svg)

**Requirement:** แยก Policy สำหรับ Client และจัดการ Local Administrator Password แบบไม่ใช้รหัสผ่านเดียวกันทุกเครื่อง

**สิ่งที่ทำ**
1. สร้าง OU สำหรับ Client และบัญชีทดสอบ
2. สร้าง GPO สำหรับ Setting ที่ตรวจผลได้ง่าย เช่น Desktop/Password-related Policy ตามสภาพแวดล้อมที่กำหนด
3. Link GPO และตรวจ Resultant Set of Policy
4. กำหนด Windows LAPS ให้สำรองรหัสผ่านของ Local Admin ไปยัง AD DS
5. บังคับให้ประมวลผล Policy และตรวจ LAPS Event/Password Metadata โดยไม่แสดงรหัสผ่านในภาพหรือ Log

**Validation / Evidence**
- `gpresult /r` หรือ HTML Report ยืนยันว่า GPO ถูก Apply
- ตรวจได้ว่า LAPS ประมวลผล Policy และมีข้อมูล Password Backup/Expiration ใน AD DS
- สามารถอธิบายได้ว่าใครควรมีสิทธิ์อ่าน/ถอดรหัส LAPS Password และเหตุใด

**Prerequisites ที่ Instructor ต้องเตรียม**
- ทำ AD Schema Extension สำหรับ Windows LAPS ล่วงหน้า (`Update-LapsADSchema`)
- ตั้ง Permission ให้ Computer Accounts เขียนข้อมูล LAPS ใน OU เป้าหมายได้ เช่น `Set-LapsADComputerSelfPermission`
- กำหนด Role/Permission สำหรับทดสอบการอ่านและถอดรหัส Password อย่างปลอดภัย
- ใช้ Domain Functional Level ที่รองรับ Password Encryption และตรวจ Policy Template ก่อนวันเรียน

**ข้อควรระวัง:** สิทธิ์อ่าน LAPS และสิทธิ์ Decrypt Password ไม่ใช่เรื่องเดียวกัน; ไม่ให้ผู้เรียน Export/ส่งต่อรหัสผ่านจริง

**Reference:** [Windows LAPS with Windows Server AD](https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-scenarios-windows-server-active-directory)

---

## Lab 03 — DNS and DHCP (45 นาที)

![DNS and DHCP](images/lab-03-dns-dhcp.svg)

**Requirement:** Client ต้องได้ IP Configuration ที่ถูกต้องและติดต่อบริการภายในด้วย DNS Name ได้

**สิ่งที่ทำ**
1. สร้าง/ตรวจ DNS A Record สำหรับ FS01 และตรวจ AD-integrated Zone
2. Configure DNS Forwarding; Conditional Forwarder ทำเฉพาะเมื่อมี DNS Target ที่ Instructor เตรียมไว้
3. Configure DHCP Scope/Exclusion/Options ใน Lab Network
4. สร้าง DHCP Reservation สำหรับ Test Client
5. เปลี่ยน CLIENT01 จากค่า IP ที่เตรียมไว้มาใช้ DHCP แล้วทดสอบ Renew

**Validation / Evidence**
- `ipconfig /all` แสดง Address, Gateway และ DNS Server ถูกต้อง
- `Resolve-DnsName FS01.corp.example.test` ตอบ IP ตามที่คาด
- Reservation ทำให้ Client ได้ IP ตามที่กำหนด
- สามารถแยกปัญหา DHCP ออกจากปัญหา DNS ได้

**Instructor Notes:** ต้องแยก DHCP Broadcast Domain ต่อ Pod และไม่มี DHCP Server ตัวอื่นมาแข่งขันกัน; FS01 ใช้ DHCP Role เพื่อความสะดวกในห้องเท่านั้น

**Stretch:** DHCP Failover (Demo)

---

## Lab 04 — Secure File Services (70 นาที)

![Secure File Services](images/lab-04-file-services.svg)

**Requirement:** แผนก Finance และ HR ใช้ Share เดียวกันได้ แต่เห็นและแก้ไขเฉพาะข้อมูลที่ได้รับอนุญาต

**สิ่งที่ทำ**
1. เตรียม Volume/Folder Structure ของ File Server
2. สร้าง AD Security Groups และ SMB Share
3. กำหนด Share Permissions และ NTFS Permissions ตาม Least Privilege
4. ทดสอบ Access จาก CLIENT01 ด้วย Authorized/Unauthorized Users
5. ทดลอง FSRM Quota หรือ File Screen หากยังมีเวลา

**Validation / Evidence**
- `\\FS01\Departments` เปิดได้จาก Client
- ผู้ใช้ที่ได้รับสิทธิ์ Modify อ่าน/เขียนใน Folder ที่กำหนดได้
- ผู้ใช้ที่ไม่มีสิทธิ์ไม่สามารถเข้าถึงหรือแก้ไขข้อมูลส่วนที่ไม่ได้รับอนุญาต
- อธิบายผลร่วมกันของ Share และ NTFS Permissions ได้
- หากทำ FSRM: แสดง Quota/File Screen ที่ทำงานจริง

**Stretch / Demo:** Azure Files หรือ Azure File Sync โดยใช้ Storage และ Sync Group ที่เตรียมไว้ล่วงหน้า ไม่ใช้เวลา Workshop นี้สร้างทุกอย่างตั้งแต่ศูนย์

---

## Lab 05 — Hyper-V Basics (35 นาที, Conditional)

![Hyper-V checkpoints and virtual switch](images/lab-05-hyper-v.svg)

**Requirement:** จัดการ Network และ Recovery Point ของ VM ทดสอบได้

**สิ่งที่ทำ**
1. ตรวจ Hyper-V Host (HV01) และ Virtual Switch ที่เตรียมไว้
2. สร้างหรือปรับ Virtual Switch และตรวจ VM Network Adapter
3. สร้าง Checkpoint บน **Test VM ที่ไม่ใช่ Domain Controller**
4. เปลี่ยนข้อมูลภายใน VM, Apply Checkpoint และตรวจการย้อนกลับ

**Validation / Evidence**
- Test VM เชื่อม Network ที่กำหนดได้
- Checkpoint/Restore ทำงานและสถานะกลับตามที่คาด
- อธิบายข้อจำกัดของ Checkpoint เทียบกับ Backup ได้

**Instructor Notes:** ต้องทดสอบ Nested Virtualization, Memory และ VM Image ก่อนวันจริง หากไม่พร้อมให้ใช้ช่วงนี้ขยาย Lab 04 หรือ Demo Azure File Sync

**Reference:** [Nested Virtualization](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization)

---

## Lab 06 — Azure Arc and Update Manager (45 นาที)

![Azure Arc and Update Manager](images/lab-06-azure-arc.svg)

**Requirement:** ดูแล On-premises Windows Server ผ่าน Azure ได้อย่างน้อยในส่วน Inventory/Connection และ Update Assessment

**สิ่งที่ทำ**
1. ตรวจ Azure Subscription, Resource Group, Permissions และ Outbound Connectivity
2. Onboard FS01 เข้าสู่ Azure Arc ด้วยแนวทางที่ Instructor กำหนด
3. ตรวจ Arc-enabled Server Resource และสถานะ Connected
4. เปิด Azure Update Manager และเรียก Check for Updates
5. ตรวจผล Assessment หรือผลตัวอย่างที่เตรียมไว้ล่วงหน้า หาก Scan ยังไม่เสร็จ

**Validation / Evidence**
- Azure Arc Resource ระบุ FS01 ของ Pod ถูกต้อง
- Connected Machine Agent แสดง Connected
- เปิดดู Update Manager Assessment/Compliance ได้
- แยกได้ว่า Arc Onboarding, Extension และ Update Assessment เป็นคนละขั้นตอน

**Instructor Notes**
- ต้องเป็น VM นอก Azure ไม่ใช่ Azure VM ที่จัดการด้วย Azure Compute อยู่แล้ว
- ไม่ทำ Patch Deployment + Reboot จริงในช่วงนี้
- ใช้ Resource Name/Resource Group ไม่ซ้ำกันในแต่ละ Pod
- เตรียมเครื่องที่ Onboard สำเร็จและตัวอย่าง Assessment สำหรับ Demo สำรอง
- ตรวจ Billing/สิทธิ์ใช้ Azure Update Manager สำหรับ Arc-enabled Server ตาม Subscription จริง

**References:** [Onboard Windows Server to Azure Arc](https://learn.microsoft.com/en-us/azure/azure-arc/servers/onboard-windows-server) และ [Update Manager Assessment](https://learn.microsoft.com/en-us/azure/update-manager/assessment-options)

---

## Lab 07 — Monitoring and Diagnostics (35 นาที)

![Windows Server monitoring and troubleshooting](images/lab-07-monitoring.svg)

**Requirement:** ตรวจ Health ของ Server และหาหลักฐานที่เกี่ยวข้องกับปัญหาได้ก่อนเริ่ม Incident

**สิ่งที่ทำ**
1. ใช้ Event Viewer ตรวจ System/Application/Directory Service Logs ที่เกี่ยวข้อง
2. ใช้ Performance Monitor ดูตัวอย่าง CPU, Memory, Disk หรือ Network Counters
3. ใช้ `dcdiag`, `repadmin`, `gpresult`, `Resolve-DnsName` และ `Test-NetConnection` ตามบทบาทของเครื่อง
4. จัดกลุ่มอาการว่าเกี่ยวกับ DNS, Network, Authentication, GPO, Storage หรือ Performance

**Validation / Evidence**
- มี Event ID/Log Source หรือ Diagnostic Result รองรับข้อสังเกต
- มีผลทดสอบพื้นฐานอย่างน้อย 3 รายการ
- ไม่สรุป Root Cause จาก Event เดียวโดยไม่มีหลักฐานสัมพันธ์กัน

**Stretch:** Azure Monitor/AMA/DCR และ Alert (Video หรือ Instructor Demo)

---

## Final Challenge — Diagnose and Recover (40 นาที)

![Troubleshooting scenario and validation](images/final-challenge.svg)

### Incident

ผู้ใช้ Domain Login ได้ แต่เข้าถึง `\\FS01\Departments` ไม่สำเร็จ และบางเครื่องมี GPO ไม่ตรงกับที่คาดไว้

Instructor จะเตรียม **Fault 1–2 จุดต่อ Pod** หลังช่วง Lab 07 โดยเลือกจาก:
- DNS Record/Client DNS Setting ไม่ถูกต้อง
- Share หรือ NTFS Permissions ไม่ตรงกับ Requirement
- GPO Link/Scope ไม่ตรงกับ OU หรือเครื่องเป้าหมาย

อย่าทำ Fault ที่ทำให้ทุก Pod ใช้งานไม่ได้พร้อมกัน และควรมี Rollback สำหรับ Fault ทุกตัว

### สิ่งที่ผู้เรียนส่ง

| สิ่งที่ตรวจ | ผ่านเมื่อ |
|---|---|
| Problem Statement | ระบุ Symptoms และขอบเขตผลกระทบชัดเจน |
| Evidence | มีผลตรวจที่สัมพันธ์กับปัญหาอย่างน้อย 2 รายการ |
| Root Cause | ระบุสาเหตุเฉพาะ ไม่ใช่เพียงอธิบายอาการ |
| Fix | แก้ Configuration/Permission โดยไม่ปิด Security Control ทั้งหมด |
| Validation | มีผลทดสอบหลังแก้จาก Client และ Authorized/Unauthorized Users |

**แนวทางการให้ Feedback:** เน้นเหตุผลและหลักฐานที่ใช้วิเคราะห์ มากกว่าการจำลำดับคลิกตามคู่มือ

## งานที่ต้องพัฒนาต่อ

- [ ] Student Guide แบบ Step-by-step เฉพาะส่วนที่ต้องใช้
- [ ] Instructor Guide / Expected Outputs / Answer Keys
- [ ] Provisioning + Reset Scripts
- [ ] Fault Injection + Rollback Scripts สำหรับ Final Challenge
- [ ] Pre-work Connection Test และ Post-work Quiz
- [ ] Smoke Test แบบรันครบ 09:00–17:00 ก่อนเปิดรุ่น

# Selected AZ-802 Lab Catalog — 18 Objectives

**Learn in the Cloud | Windows Server 2025**

เอกสารนี้บันทึกรายการ **18 Skill Objectives / 34 Selected Activities** สำหรับใช้พัฒนา Recorded Video, Guided Labs และ Workshop ทั้งสอง Track

> **สถานะ:** รายการหัวข้อที่เลือกสำหรับพัฒนาหลักสูตร ไม่ใช่คำยืนยันว่าในวัน Onsite จะทำครบ 34 Activities แบบ End-to-End ทั้งหมด เนื้อหาที่เปิดสอนจริงและเวลาต่อ Lab จะยืนยันหลัง Dry Run

อ้างอิง [Microsoft AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) (6 July 2026)

## แนวทางการจัด Lab

- **Hands-on:** ผู้เรียน Configure และ Verify ด้วยตนเอง
- **Guided:** เตรียม Guest VM Images, Services, Tenants หรือ Prerequisites แล้วให้ผู้เรียนทำขั้นตอนที่มีคุณค่าสำคัญ
- **Demo:** Instructor สาธิต Feature ที่ต้องใช้เวลา/ทรัพยากรมาก หรือแสดงพฤติกรรมระบบที่เตรียมพร้อมไว้
- **Video:** Concepts และ Features อื่นใน Exam Objectives ที่ไม่ได้เลือกเป็น Hands-on

การแบ่ง Track ข้างล่างเป็น **ข้อเสนอสำหรับจัดตาราง** ไม่ใช่การเปลี่ยนกำหนดการ Workshop ที่ประกาศแล้ว

## Selected Objectives

| # | Microsoft Skill Objective | Selected Activities | Proposed Track | Lab Approach |
|---:|---|---|---|---|
| 01 | Deploy and manage AD DS domain controllers | Promote first DC; manage FSMO | 1 | Guided |
| 02 | Configure and manage multi-site, multi-domain, and multi-forest environments | Configure AD Sites; add additional DC | 1 | Guided |
| 03 | Create and manage AD DS security principals | Create users; create groups | 1 | Hands-on |
| 04 | Manage Windows Server by using domain-based Group Policies | Implement GPO | 1 | Hands-on |
| 05 | Configure remote management for Windows Server instances in a hybrid environment | Install Windows Admin Center (WAC) | 1 | Guided |
| 06 | Manage Windows Server instances and workloads by using Azure services in a hybrid environment | Implement Azure Arc; Azure Update Manager | 2 | Guided |
| 07 | Manage Hyper-V and guest VM | Install/configure Hyper-V; enable nested virtualization | 2 | Guided |
| 08 | Manage Windows Server VMs in Azure | Create Azure VM; create VM scale set | 2 | Guided |
| 09 | Implement on-premises and hybrid name resolution | Configure DNS | 1 | Hands-on |
| 10 | Manage IP addressing in on-premises and hybrid scenarios | Implement DHCP Failover | 1 | Guided |
| 11 | Configure and manage Azure Files | Implement Azure File Share; Azure File Sync | 2 | Guided |
| 12 | Configure and manage Windows Server file shares | File share permissions; FSRM; DFS | 1 | Hands-on / Guided |
| 13 | Configure Windows Server storage | Implement S2D | 2 | Guided |
| 14 | Secure Windows Server operating system | Server hardening; Windows LAPS | 1 | Hands-on / Guided |
| 15 | Secure AD DS | Entra Connect Sync; Entra Password Protection for AD DS; AD hardening; AD delegation | 2 | Guided |
| 16 | Monitor by using Windows Server tools and Azure services | Performance monitoring | 1 | Hands-on |
| 17 | Troubleshoot Windows Server issues | Basic connectivity; name resolution; time sync troubleshooting | 1 | Hands-on |
| 18 | Troubleshoot Active Directory | Enable AD Recycle Bin; mini AD health check | 1 | Hands-on |

**Proposed split:** Track 1 = 12 Objectives; Track 2 = 6 Objectives. เป็นเพียงการจัดตาม Dependency/Technology ก่อนทำ Full Dry Run; ไม่ใช่การแบ่งเวลา 12:6 หรือการรับประกันว่า 1 Objective เท่ากับ 1 Lab

## จุดที่ต้องเตรียมก่อนวัน Workshop

### AD DS — First DC, Additional DC, Sites และ FSMO
- เตรียม Windows Server Guest Images แบบยังไม่ Promote สำหรับ **First DC**
- เมื่อ First DC ถูก Promote แล้วจึงเพิ่ม Additional DC และสร้าง Sites/Subnets/Replication ตรวจผล
- FSMO เน้น Locate Roles, Transfer (ตามเวลา) และตรวจหลังเปลี่ยน; ไม่ทำ Seize Role โดยไม่จำเป็น
- **Configure sites** ไม่ได้หมายความว่าจะต้องติดตั้ง Multi-domain หรือ Multi-forest ทั้งหมด ชื่อหัวข้อเป็นชื่อ Skill Objective จาก Microsoft

### WAC, DNS, DHCP Failover และ DFS
- WAC ติดตั้งบน Dedicated Management Server/Prepared VM ไม่ใช่บังคับติดตั้งบน DC
- DHCP Failover ต้องมี **DHCP Servers สองตัวที่ถูก Configure/Authorize** และต้องแยก Network Segments ของแต่ละ Student Pod
- DFS เลือก **DFS Namespace** เป็นหัวข้อเริ่มต้น; DFS Replication เพิ่มเป็น Guided Step/Demo ถ้ามีเวลา
- AD-integrated DNS แสดง Forwarders/Records และ Name Resolution; ไม่จำเป็นต้อง Deploy DNSSEC ใน Onsite

### Hyper-V, Azure VM และ VM Scale Sets
- ใช้ Azure VM Size ที่รองรับ Nested Virtualization พร้อม **Standard Security Type** และติดตั้ง Hyper-V Host/Guest VM Images ล่วงหน้า
- บท Nested Hyper-V มีเป้าหมายให้ผู้เรียนเข้าใจการ Expose CPU Virtualization Extensions และ **สร้าง Empty VM + Virtual Switch/VHDX** ไม่ต้องลง Guest OS
- หาก Nested VM ที่ใช้สอนอยู่ภายใน Azure Hyper-V Host อยู่แล้ว การติดตั้ง Hyper-V เพิ่มอีกชั้นหนึ่งต้องผ่าน Compatibility Test และไม่รับประกัน Triple-Nesting ทุก Configuration
- Azure VM/VMSS ทำเป็น Guided Lab ด้วย Image/Network/RBAC/Quota ที่เตรียมไว้ และยืนยัน Deployment Result ก่อน Cleanup เพื่อควบคุมค่าใช้จ่าย

### Azure Hybrid, Files และ S2D
- สำหรับ Arc ให้ทดลองกับ Guest Server ที่ไม่ได้ถูกบริหารเป็น **Native Azure VM Resource**; ห้ามใช้ Native Azure VM แล้วโฆษณาว่าเป็น Production Arc Deployment
- Azure File Share ต้องเตรียม Storage/Identity/Network Connectivity; File Sync ต้องมี Registered Server Agent, Sync Service และ Endpoint ที่พร้อม
- S2D Lab: **2 Guest Nodes + Witness**, Windows Server **Datacenter**, อย่างน้อย **2 Data Disks ต่อ Node** ไม่รวม OS Disk
- เป้าหมาย S2D คือ Enable/Create Storage Pool และตรวจผล; ไม่บังคับ Simulate Full Cluster Failover, Live Migration หรือ Install OS
- ถ้า Guest Nodes อยู่ใต้ Azure VM Host เดียวกัน เป็น Evaluation/Training Lab ไม่ใช่ Host Failure Tolerance
- ไม่ใช้ Host-level Virtual Disk Snapshot เป็น Recovery/Reset Method ที่อ้างว่ารองรับสำหรับ S2D Guest Cluster

### Windows Server / AD Security
- Windows Server Hardening ควรกำหนด 3–5 Controls ที่ตรวจผลได้จริง เช่น Firewall Policy, Audit Policy, Local Account Settings หรือ Microsoft Security Baseline เลือกตาม Lab Image
- Windows LAPS: เตรียม AD Schema/Permissions และ Policy Prerequisites แล้วให้ผู้เรียนตรวจ Backup/Rotation
- **Entra Connect Sync** เพิ่มเป็น Hybrid Identity Lab ภายใต้หัวข้อ Secure AD DS เพื่อเชื่อมโยงการเรียน แต่ *ไม่ใช่ Bullet ของ Skill Objective นี้โดยตรง* ใน Study Guide
- Entra Connect ต้องมี Verified Domain/UPN ที่ Sync ได้, Tenant และ Domain-joined Member Server ที่รองรับ; แยกจาก Domain Controller
- **Entra Password Protection for AD DS** ต้องมี Proxy + DC Agent + Licensing เหมาะสม และเริ่มจาก **Audit Mode** ก่อน Enforce
- **AD Hardening:** เริ่มจาก Password Policy, Privileged Group Review, DC Security Controls (เฉพาะสิ่งที่ไม่ทำให้ Lab ใช้งานไม่ได้)
- **AD Delegation:** สร้าง OU และมอบสิทธิ์ให้ Account ทดสอบโดยไม่ต้องเป็น Domain Admin

### Monitoring / Troubleshooting
- Performance Monitoring เน้น **PerfMon + Data Collector Set** และการตีความผล
- Basic Troubleshooting เน้น **Network/Firewall → DNS → Time/Kerberos → Windows Services/Logs** ตาม Evidence
- AD Recycle Bin และ Mini Health Check เป็น Lab สั้น ๆ โดยดู `dcdiag`, `repadmin`, DNS และ Event Logs

## เวลาและความคาดหวัง

Workshop มีเวลาปฏิบัติ **405 นาทีต่อ Track** (09:00–17:00 รวม Lunch/Break 75 นาที) รวม 2 Tracks = **810 นาที**

รายการ 34 Activities นี้ต้องแบ่งเป็น Hands-on Core, Guided Steps และ Short Demos โดยอาศัย **Prepared Images / Pre-configured Azure Resources / Staged Snapshots**; ถ้าต้องการให้ลงมือ Configure ทุก Feature ตั้งแต่ต้นจนจบจริง ต้องเพิ่มวันเรียนหรือแยก Extended Lab

สำหรับหน้า Public ไม่ควรโฆษณาว่า **34 Complete Labs in 2 Days** จนกว่าจะมี Full Dry Run ที่พิสูจน์ได้

## References

- [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802)
- [Nested Virtualization](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enable-nested-virtualization)
- [S2D in Guest VMs](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-spaces-direct-in-vm)
- [Entra Connect Sync Prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-install-prerequisites)
- [On-premises Entra Password Protection](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-password-ban-bad-on-premises-deploy)

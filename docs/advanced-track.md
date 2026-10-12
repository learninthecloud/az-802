# Track 2 — Advanced Infrastructure (Proposed)

> Course design proposal · 12 October 2026. ยังไม่ใช่กำหนดการหรือคำยืนยันว่า Lab ทุกหัวข้อพร้อมเปิดสอน

**Format:** Recorded Video (Pre-work) + Onsite Workshop 1 วัน 09:00–17:00
**Platform:** Windows Server 2025, Hyper-V, Active Directory, Microsoft Azure (เฉพาะบาง Demo)
**Project:** Build a Resilient Windows Server Infrastructure

![Advanced S2D cluster mental model](images/advanced-s2d-cluster.svg)

## เป้าหมาย

จาก Track 1 ที่เน้น Deploy, Configure, Validate และ Troubleshoot ไปสู่ **High Availability, Resilience, Disaster Recovery และ Secure Access** โดยให้ผู้เรียนอธิบายได้ว่าอะไรยังทำงานต่อเมื่อ Node/Storage/Network บางส่วนล้มเหลว และอะไรยังต้องใช้ Recovery Process

Track 2 **ไม่จำเป็นต้องเรียน Track 1 ก่อน** หากมีความรู้ Windows Server/AD DS/DNS/SMB, PowerShell และ Hyper-V เทียบเท่า แต่ควรทำ Pre-work/Readiness Check

## Track 1 vs Track 2

| | Track 1 — Administration | Track 2 — Advanced Infrastructure |
|---|---|---|
| Outcome | Configure service and verify it works | Prove failure behavior and recovery boundary |
| Labs | AD DS, GPO/LAPS, DNS/DHCP, SMB, Azure Arc, Diagnostics | Failover Cluster, S2D/CSV, Node Failure, Live Migration, SMB over QUIC |
| Duration | 1 วัน | 1 วันแบบเข้มข้น (ต้องเตรียม Environment) |
| Main question | ทำงานได้ไหม? | เมื่อมีความเสียหาย ระบบยังให้บริการได้แค่ไหน? |

## WOW Feature Backlog

| Feature | สิ่งที่ผู้เรียนจะได้เห็น | Priority | Delivery |
|---|---|---|---|
| Storage Spaces Direct (S2D) | Local Disks บนหลาย Node รวมเป็น Resilient Pool | Must | Core hands-on |
| Failover Clustering + Quorum + CSV | Cluster Node ถูกหยุด แต่ Storage/Clustered Workload มี Recovery Behavior ที่ตรวจสอบได้ | Must | Core hands-on |
| Hyper-V Highly Available VM / Live Migration | ย้าย Running VM ระหว่าง Hosts | Must learning objective | Hands-on เมื่อมี Cluster ที่เตรียมไว้; ไม่พร้อมให้ Instructor Demo |
| SMB over QUIC | Windows 11 เข้า File Share ผ่าน UDP 443 โดยไม่ต้องเปิด TCP 445 ใน Test Path | Must | Core hands-on |
| Storage Replica | Replicate Volume สำหรับ Site-level DR | Should | Guided Demo / Extended Lab |
| Hyper-V Replica | Replicate VM และทดสอบ VM Recovery | Should | Guided Demo / Extended Lab |
| Azure File Sync / Cloud Tiering | Local Cache ร่วมกับ Cloud File Share | Should | Extended Lab |
| Windows Server 2025 Hotpatch + Azure Arc | Update บางประเภทโดยไม่ต้อง Restart | Should | Enrollment/Status Demo |
| AD Recovery: Recycle Bin / DSRM / SYSVOL | กู้ Objects หรือแก้ปัญหา AD | Should | Advanced Identity Extension |
| JEA / OSConfig / Credential Guard | Least-privilege Admin / Security Hardening | Should | Security Extension |
| SMB Direct / RDMA / SET | ออกแบบ Low-latency Storage Networking | Demo | Hardware-dependent |
| ReFS / Storage QoS / Dedup | Storage Efficiency และ Performance | Optional | Video / Extension |
| RODC / Trust / AD Sites | Multi-site and multi-forest scenarios | Optional | Identity Extension |
| GPU Partitioning / Azure Local | Advanced virtualization platform capabilities | Future | Separate course |

**อย่าพยายามทำทุก Feature ภายใน 1 วัน**; Core Hands-on ต้องทำแล้วมีหลักฐานตรวจผลได้ ส่วน Optional/Extended ให้มี Video หรือ Advanced 2-day รุ่นถัดไป

## Draft Schedule — 09:00–17:00

| Time | Duration | Topic | Evidence / Output |
|---|---:|---|---|
| 09:00–09:20 | 20m | Scenario / Failure Domains / RTO-RPO | ระบุ Success Criteria |
| 09:20–10:20 | 60m | A01 — Failover Cluster, Validation, Witness | Cluster/Nodes/Quorum Healthy |
| 10:20–11:45 | 85m | A02 — S2D Storage Pool + ReFS/CSV | Virtual Disk และ CSV Online |
| 11:45–12:00 | 15m | Storage Checkpoint | Storage Health Evidence |
| 12:00–13:00 | 60m | Lunch | — |
| 13:00–13:55 | 55m | A03 — Controlled Node Failure / Recovery | ขอบเขตความทนทานและการฟื้นตัว |
| 13:55–14:45 | 50m | A04 — Hyper-V Live Migration (Conditional) | Running VM ย้ายระหว่าง Hosts |
| 14:45–15:00 | 15m | Break | — |
| 15:00–15:55 | 55m | A05 — SMB over QUIC | ตรวจ Connection ผ่าน QUIC |
| 15:55–16:25 | 30m | DR Showcase — Storage Replica **หรือ** Hyper-V Replica | อธิบาย Recovery Workflow |
| 16:25–17:00 | 35m | Final Incident / Review | Root Cause + Validation |

**สถานะ:** Pilot Target เท่านั้น; ต้องจับเวลา Dry Run กับจำนวน Pods และ Network จริงก่อนเปิดขาย

## Lab Expectations

### A01 — Failover Cluster / Quorum
- ตรวจ Cluster Nodes, Name Resolution และ Cluster Validation
- เตรียม File Share/Cloud Witness แล้วให้ผู้เรียนตรวจ Quorum Configuration
- Evidence: Cluster Validation Report, Cluster Nodes/Quorum Status

### A02 — S2D / Storage Resiliency
- ตรวจ Disks ที่เตรียมไว้บน 2 Nodes (แยก OS Disk ออกจาก Data Disks)
- เปิด S2D/ตรวจ Storage Pool, Virtual Disk, ReFS Volume และ CSV
- Evidence: Storage Pool Health, Volume Health และ CSV Path
- ไม่ให้ผู้เรียนรันคำสั่งลบดิสก์โดยไม่มี Disk Inventory/Scope ของ Disposable Lab Disk

### A03 — Failure and Recovery
- ทำ Planned Drain หรือ Controlled Node Outage ใน Pod ที่แยกจากระบบจริง
- ตรวจความเปลี่ยนแปลงของ Quorum, Storage, Clustered Workload และ Client Behavior
- ต้องมี **Workload ที่รองรับและถูก Cluster แล้ว** ก่อนจะอ้างว่า Service Continues
- การที่ CSV Online ไม่เท่ากับทุก Application ไม่มี Downtime

### A04 — Hyper-V Live Migration
- ใช้ Hyper-V Cluster ที่เตรียมไว้แยกจาก S2D VM Guest Cluster ได้ เพื่อหลีกเลี่ยง Double-nesting และภาระ Compute
- ตรวจ Owner Node และ Client Connectivity ระหว่าง Migration
- แยก Planned Live Migration ออกจาก Unplanned Failover
- ถ้า Shared Instructor Cluster เท่านั้น ให้ระบุชัดว่าเป็น Demo ไม่ใช่ทุกคนได้ทำ Hands-on

### A05 — SMB over QUIC
- Windows Server 2025 + Windows 11 + Trusted Certificate + DNS + UDP/443 ใน Isolated Test Network
- จำลอง Remote Client โดย Block TCP/445 ในเส้นทางทดสอบ
- ตรวจว่า SMB ใช้ QUIC จริง และสิทธิ์เข้าถึง File Share ยังถูกต้อง
- การใช้ QUIC ไม่ได้ทำให้ Authentication/Authorization ไม่จำเป็น; สำหรับ External Kerberos Access ต้องออกแบบ KDC Proxy อย่างเหมาะสม

### DR Showcase — เลือกหัวข้อเดียว
- Storage Replica: Sync/Async, Data Volume vs Log Volume, Failover และ RPO/RTO
- Hyper-V Replica: Replication Health, Test/Planned Failover, Recovery Point
- 30 นาทีใช้ Environment ที่ Replicate ไว้ก่อน; ไม่ใช่ Full Deployment
- Replication ไม่ใช่ Backup; ต้องมี Backup/Restore และการป้องกัน Logical Corruption แยก

## Prerequisites ที่ต้องยืนยันก่อนเปิด Track 2

1. **S2D ต้องใช้ Windows Server Datacenter Edition**; Windows Server Standard ไม่เพียงพอ
2. S2D Guest VM Cluster รองรับ **2–3 Nodes**; แบบ 2 Nodes **ต้องมี Witness**
3. ใน VM Guest Cluster ต้องมีอย่างน้อย **2 Virtual Data Disks ต่อ Node** และใช้สภาพแวดล้อม Disk/Network ที่ผ่าน Preflight
4. เอกสาร Microsoft ระบุว่า **Host-level Virtual Disk Snapshot/Restore ไม่รองรับ** สำหรับ S2D Guest VM Cluster: จึงต้องออกแบบ Reset/Rebuild/Guest-aware Backup แทน
5. ถ้า S2D Nodes เป็น VMs ที่อยู่บน Physical Host เดียวกัน การปิด Node หนึ่งเครื่องเป็นเพียง **Guest Node Failure Simulation** ไม่สามารถอ้างความทนทานต่อ Host Failure ได้
6. Production S2D ต้องใช้ Hardware/Network ที่ตรวจสอบความเข้ากันได้; VM Workshop เป็น **Evaluation Lab** ไม่ใช่ Certified Production Reference
7. Live Migration Lab ต้องมี Hyper-V Hosts/Storage/Network ที่รองรับและผ่านการทดสอบ; อาจต้องใช้ Shared Instructor Cluster แทน Pod ส่วนตัว
8. สำหรับ 20–25 คน ต้องทำ Capacity/Cost Test ก่อนเลือกระหว่าง 10–13 Pods กับ Shared Cluster + Group Rotation
9. Hotpatch บางเดือนเป็น Baseline Update ซึ่งยังต้อง Restart; ไม่รับประกันว่าจะมี Patch ให้ติดตั้งจริงในวันเรียน

## Next Steps

- [ ] Smoke Test A01–A03 บน 2-Node S2D Guest Cluster จริง
- [ ] ทดสอบ Witness, Node Outage, Cluster Health และ Recovery
- [ ] ตัดสินใจว่าจะให้ทุกกลุ่มทำ Live Migration หรือใช้ Instructor Cluster
- [ ] เตรียม Certificate, QUIC Server/Client และ Packet/Connection Validation
- [ ] ทดลอง Runtime/Cost กับจำนวนผู้เรียนเป้าหมาย
- [ ] ทำ Student Guide + Expected Results + Reset/Rebuild Plan
- [ ] พิจารณา **Advanced Extended 2-Day** สำหรับ Live Migration, Storage Replica, Hyper-V Replica, Recovery และ Hybrid Advanced Features เต็มรูปแบบ

## Microsoft References

- [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802)
- [Deploy S2D](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/deploy-storage-spaces-direct)
- [S2D in Guest VMs](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-spaces-direct-in-vm)
- [Hyper-V Live Migration](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/live-migration-overview)
- [SMB over QUIC](https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-over-quic)
- [Arc-enabled Hotpatch](https://learn.microsoft.com/en-us/windows-server/get-started/enable-hotpatch-azure-arc-enabled-servers)

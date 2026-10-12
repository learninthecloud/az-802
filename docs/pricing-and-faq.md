# ค่าเรียนและคำถามที่พบบ่อย

## ค่าเรียน

| หลักสูตร | Workshop | ราคา |
|---|---|---:|
| Track 1 — Administration | 1 วัน (09:00–17:00) | 5,750 บาท |
| Track 2 — Advanced & Hybrid | 1 วัน (09:00–17:00) | 5,750 บาท |
| **Track 1 + Track 2** | 2 วัน (วันละ Track) | **10,500 บาท** |

หลักสูตรประกอบด้วย Recorded Video/Pre-work และ Onsite Workshop ตาม Track ที่เลือก รายละเอียดสิทธิ์รับชมวิดีโอ วันจัดอบรม สถานที่ VAT และเงื่อนไขการลงทะเบียนจะแจ้งเมื่อเปิดรับสมัคร

## FAQ

### Track 1 กับ Track 2 ต่างกันอย่างไร?

Track 1 เน้น Windows Server Administration ได้แก่ First/Additional DC, AD Sites, FSMO, Users/Groups, GPO, Windows Admin Center, DNS, DHCP Failover, File Share/FSRM/DFS, Server Hardening/LAPS, Monitoring และ Troubleshooting

Track 2 เน้น Advanced & Hybrid ได้แก่ Azure Arc/Update Manager, Hyper-V/Nested Virtualization, Azure VM/VMSS, Azure Files/File Sync, S2D และ Hybrid Identity (Entra Connect Sync, Entra Password Protection for AD DS, AD Hardening/Delegation) โดยใช้ Prepared VM Images เพื่อไม่เสียเวลาติดตั้ง OS

### ต้องเรียน Track 1 ก่อนหรือไม่?

**ไม่จำเป็น** ถ้าดูแล Windows Server, AD DS, DNS, Storage, Hyper-V และ PowerShell ได้อยู่แล้ว สามารถเลือก Track 2 โดยตรง

### สามารถเลือกแค่หนึ่ง Track ได้ไหม?

ได้ Track ละ 5,750 บาท ไม่บังคับลงทั้งสอง

### เรียนทั้งสอง Track จะมีเวลา Onsite กี่วัน?

2 วัน (วันละ Track) และมี Recorded Video/Pre-work ตามหัวข้อ ไม่ใช่คอร์ส 2 Track ที่ยัดรวมในวันเดียว

### ต้องใช้ Server กี่เครื่องใน Track 2?

ใน Logical Architecture มี DC01, SYNC01 (Entra Connect), FS01 (File Server/File Sync/Witness), S2D01, S2D02 และ CLIENT01 โดยทดลองบน Azure VM ขนาดใหญ่ที่เป็น Nested Hyper-V Host

**Logical Roles ไม่ใช่จำนวน VM จริงที่ผู้เรียนต้องสร้างทั้งหมด** ผู้สอนเตรียม Guest VM Images ไว้ก่อน และสามารถรวม Roles บางส่วนเพื่อประหยัด Resources ได้ตามความเหมาะสม [ดู Lab Topology](lab-topology.md)

### Track 2 ต้องติดตั้ง Windows Server ใหม่ในห้องไหม?

**ไม่ต้อง** ผู้สอนเตรียม Images และ Guest VMs ไว้แล้ว บท Nested Hyper-V ตั้งเป้าสร้าง **Virtual Machine เปล่าโดยไม่ติดตั้ง Guest OS** ส่วน S2D ตั้งเป้า Enable/สร้าง Storage ให้เห็นผล ไม่ใช่สร้าง Production Cluster ทั้งระบบ

### S2D จะมี Failover Test และ Live Migration หรือไม่?

ไม่ใช่ Outcome ที่บังคับของ Track 2 รุ่น 1 วัน ผู้เรียนจะฝึก Enable/Configure และ Verify Cluster/S2D ก่อน ส่วน HA/DR ขั้นสูงไม่อยู่ในรายการ Hands-on หลักของ Track 2

### มีคอมพิวเตอร์ Lab ให้ไหม?

Lab Environment อยู่บน Microsoft Azure และ Windows Server VM ที่เตรียมไว้ ผู้เรียนต้องนำ Laptop มาเชื่อมต่อผ่านวิธีที่ผู้สอนกำหนด รายละเอียดขั้นต่ำจะแจ้งก่อนวันเรียน

### เรียนแล้วสอบ AZ-802 ผ่านแน่ไหม?

ไม่ได้รับประกันผลสอบ เนื้อหาอ้างอิง [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) แต่ Workshop คัดเฉพาะหัวข้อที่เหมาะกับการทดลองในวันเดียว ไม่ใช่การฝึกทุก Skill แบบครบถ้วน

### จองที่นั่งหรือจ่ายเงินได้แล้วหรือยัง?

**ยังไม่เปิดรับสมัครผ่าน GitHub** กำหนดการ สถานที่ และช่องทางสมัครจะประกาศหลังจาก Lab และรายละเอียดการจัดอบรมได้รับการยืนยัน

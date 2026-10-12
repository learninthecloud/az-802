# ค่าเรียนและคำถามที่พบบ่อย

## Package และราคา

| Package | Workshop | ราคา |
|---|---|---:|
| **Track 1 — Administration** | 1 วัน (09:00–17:00) | **5,750 บาท** |
| **Track 2 — Advanced Infrastructure** | 1 วัน (09:00–17:00) | **5,750 บาท** |
| **Both Tracks** | 2 วัน (วันละ Track) | **8,625 บาท** |

**สูตรราคา 2 Tracks:** 5,750 + (5,750 ÷ 2) = **8,625 บาท**

เทียบกับซื้อแยก 11,500 บาท ประหยัด **2,875 บาท (25%)**  
หรือคิดง่าย ๆ ว่า **Track ที่ 2 ลด 50%** เมื่อซื้อแพ็กเกจ 2 Tracks

ทุกแพ็กเกจมี Recorded Video/Pre-work สำหรับการเตรียมตัวในหัวข้อที่เกี่ยวข้องและการเข้า Workshop ตาม Track ที่เลือก **รายละเอียดสิทธิ์รับชมและระยะเวลาจะประกาศตอนเปิดลงทะเบียน**

> ราคาข้างต้นเป็น **แผนราคาเปิดหลักสูตร** ยังไม่ใช่การเปิดรับชำระเงินจริง ก่อนเปิดรับสมัครจะยืนยัน VAT, อาหาร/เครื่องดื่ม, สถานที่, วันอบรม, จำนวนที่นั่ง, การเลื่อน/คืนเงิน และเงื่อนไขการใช้ส่วนลดอีกครั้ง

## FAQ

### Track 1 กับ Track 2 ต่างกันอย่างไร?

Track 1 เน้นการดูแล Windows Server ให้ใช้งานได้ เช่น AD DS, Group Policy, DNS/DHCP, File Server, Azure Arc และ Troubleshooting

Track 2 เน้น Advanced Infrastructure เช่น Failover Cluster, S2D, Nested Hyper-V และ SMB over QUIC โดยผู้เรียนใช้ VM Images ที่เตรียมไว้เพื่อโฟกัสที่ Feature ไม่ใช่การลง OS

### ต้องเรียน Track 1 ก่อนหรือไม่?

**ไม่จำเป็น** ถ้าดูแล Windows Server, AD DS, DNS, Storage, Hyper-V และ PowerShell ได้อยู่แล้ว สามารถเลือก Track 2 โดยตรง

### สามารถเลือกแค่หนึ่ง Track ได้ไหม?

ได้ Track ละ 5,750 บาท ไม่บังคับลงทั้งสอง

### เรียนทั้งสอง Track จะมีเวลา Onsite กี่วัน?

2 วัน (วันละ Track) และมี Recorded Video/Pre-work ตามหัวข้อ ไม่ใช่คอร์ส 2 Track ที่ยัดรวมในวันเดียว

### Track 2 ต้องติดตั้ง Windows Server ใหม่ในห้องไหม?

**ไม่ต้อง** ผู้สอนเตรียม Images และ Guest VMs ไว้แล้ว บท Nested Hyper-V ตั้งเป้าสร้าง **Virtual Machine เปล่าโดยไม่ติดตั้ง Guest OS** ส่วน S2D ตั้งเป้า Enable/สร้าง Storage ให้เห็นผล ไม่ใช่สร้าง Production Cluster ทั้งระบบ

### S2D จะมี Failover Test และ Live Migration หรือไม่?

ไม่ใช่ Outcome ที่บังคับของ Track 2 รุ่น 1 วัน ผู้เรียนจะฝึก Enable/Configure และ Verify Cluster/S2D ก่อน ส่วน HA/DR ขั้นสูงอาจเป็น Demo หรือหัวข้อในหลักสูตรต่อยอด

### มีคอมพิวเตอร์ Lab ให้ไหม?

Lab Environment อยู่บน Microsoft Azure และ Windows Server VM ที่เตรียมไว้ ผู้เรียนต้องนำ Laptop มาเชื่อมต่อผ่านวิธีที่ผู้สอนกำหนด รายละเอียดขั้นต่ำจะแจ้งก่อนวันเรียน

### เรียนแล้วสอบ AZ-802 ผ่านแน่ไหม?

ไม่ได้รับประกันผลสอบ เนื้อหาอ้างอิง [AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802) แต่ Workshop คัดเฉพาะหัวข้อที่เหมาะกับการทดลองในวันเดียว ไม่ใช่การฝึกทุก Skill แบบครบถ้วน

### จองที่นั่งหรือจ่ายเงินได้แล้วหรือยัง?

**ยังไม่เปิดรับสมัครผ่าน GitHub** กำหนดการ สถานที่ และช่องทางสมัครจะประกาศหลังจาก Lab และรายละเอียดการจัดอบรมได้รับการยืนยัน

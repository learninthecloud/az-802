# Windows Server 2025 — Hands-on Project Workshop

**Learn in the Cloud | AZ-802: Administering Windows Server**

เรียน Concepts ผ่าน Recorded Video ก่อนมา Workshop แล้วลงมือทำจากโจทย์ที่ใกล้เคียงงานจริงบน Windows Server 2025 และ Microsoft Azure

มี **2 Tracks** ให้เลือกเรียนแยกกันได้ แต่ละ Track เป็น Workshop **1 วัน เวลา 09:00–17:00** ผู้เรียนไม่จำเป็นต้องลงทะเบียนทั้งสอง Track

> **สถานะ:** กำลังเตรียมเปิดรุ่นแรก ตารางเรียนและรายละเอียดการสมัครจะประกาศภายหลัง ราคาด้านล่างเป็นราคาที่เสนอสำหรับเปิดหลักสูตร ยังไม่ใช่หน้ารับชำระเงิน

## เลือก Track ที่เหมาะกับคุณ

| | Track 1 — Administration | Track 2 — Advanced Infrastructure |
|---|---|---|
| เหมาะกับ | IT Support, System Administrator, ผู้เริ่มดูแล Server | System Administrator และ Infrastructure Engineer ที่มีพื้นฐานแล้ว |
| เป้าหมาย | Configure ระบบให้ใช้งานได้ ตรวจสอบและแก้ปัญหาเป็น | เข้าใจ Storage, Virtualization และ Advanced Server Features ผ่าน Lab |
| Hands-on | AD DS, GPO/LAPS, DNS/DHCP, SMB, Azure Arc, Monitoring | Failover Cluster, **Storage Spaces Direct (S2D)**, Hyper-V Nested Lab, SMB over QUIC |
| รูปแบบ | Recorded Video + Onsite 1 วัน | Recorded Video/Pre-work + Onsite 1 วัน |
| รายละเอียด | [Track 1 Course Outline](docs/course-outline.md) | [Track 2 Course Outline](docs/advanced-track.md) |

### Track 1 / Administration

![Track 1 — Windows Server Lab Topology](docs/images/lab-architecture.svg)

เริ่มจาก Domain Controller, DNS/DHCP และ Group Policy แล้วต่อยอดไป File Services, Windows LAPS, Azure Arc และ Troubleshooting โดยใช้ Environment เดียวตลอดวัน

[ดูหัวข้อและตาราง Track 1](docs/workshop-plan.md)

### Track 2 / Advanced Infrastructure

![Track 2 — S2D Cluster Mental Model](docs/images/advanced-s2d-cluster.svg)

ใช้ **Azure VM ขนาดใหญ่เป็น Hyper-V Host** และเตรียม Windows Server Guest VM Images ไว้ก่อนเริ่มเรียน เพื่อใช้เวลาที่มีไปกับการทดลอง Features มากกว่าการติดตั้ง OS

แกนหลักของ Track 2 คือสร้าง Failover Cluster และทดลอง **Enable S2D / Create Storage Pool** ให้สำเร็จ พร้อมฝึกสร้าง **Virtual Machine เปล่า (ไม่ติดตั้ง OS)** ในบท Nested Hyper-V และทำ Lab/Guided Demo ฟีเจอร์ขั้นสูงที่คัดเลือกไว้

**ขอบเขตที่ชัดเจน:** เป็น Lab สำหรับเรียนรู้แนวคิดและ Configuration ไม่ใช่การ Deploy Production HA Cluster หรือทดสอบ Failover ทุกกรณี

[ดูหัวข้อและตาราง Track 2](docs/advanced-track.md)

## ค่าเรียน (ราคาที่เสนอ)

| Package | สิ่งที่ได้รับ | ราคา |
|---|---|---:|
| **1 Track** | Recorded Video/Pre-work + Onsite Workshop 1 วัน (เลือก Track 1 หรือ 2) | **5,750 บาท** |
| **2 Tracks** | ทั้ง Track 1 และ Track 2 รวม Onsite Workshop 2 วัน | **8,625 บาท** |

**2 Tracks ประหยัด 2,875 บาท (25%)** จากราคาปกติรวม 11,500 บาท โดย Track ที่สองลด 50%

เงื่อนไขเกี่ยวกับ VAT, อาหาร/เครื่องดื่ม, วันจัดอบรม, จำนวนที่นั่ง และวิธีสมัครจะยืนยันในประกาศเปิดรับสมัคร

[รายละเอียดแพ็กเกจและคำถามที่พบบ่อย](docs/pricing-and-faq.md)

## แนวทางการเรียน

- **ก่อนมา Onsite:** ดู Recorded Video/Pre-work และทบทวนเนื้อหาพื้นฐานของ Track ที่เลือก
- **ใน Workshop:** รับ Requirements, ลงมือทำ Configuration ด้วยตนเอง และตรวจผลด้วยเครื่องมือจริง
- **หลังทำ Lab:** เข้าใจว่า Feature ทำอะไร ใช้เมื่อใด และจะตรวจสอบได้อย่างไรว่าทำงานตามที่คาดไว้

Lab Environment ใช้ Windows Server 2025 และ Microsoft Azure โดยผู้สอนเตรียม Images, Accounts และ Configuration ที่ใช้เวลานานให้ล่วงหน้า เพื่อให้ผู้เรียนโฟกัสที่โจทย์หลัก

## คุณควรมีพื้นฐานอะไร?

**Track 1:** Windows Client/Server พื้นฐาน, IP Address, DNS และใช้ PowerShell ได้บ้าง

**Track 2:** AD DS, DNS, Storage, Hyper-V และ PowerShell ระดับใช้งานได้จริง **ไม่จำเป็นต้องเรียน Track 1 ก่อน** ถ้ามีพื้นฐานเทียบเท่า

## เอกสารหลักสูตร

- [Track 1 — Course Outline](docs/course-outline.md)
- [Track 1 — Workshop Schedule](docs/workshop-plan.md)
- [Track 1 — Lab Topics](docs/lab-briefs.md)
- [Track 2 — Advanced Infrastructure](docs/advanced-track.md)
- [ค่าเรียนและ FAQ](docs/pricing-and-faq.md)

**Reference:** [Microsoft Learn — AZ-802 Study Guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-802)

หลักสูตรนี้พัฒนาโดย Learn in the Cloud ไม่ใช่หลักสูตรที่จัดหรือรับรองอย่างเป็นทางการโดย Microsoft การเรียน Workshop ไม่ได้ยืนยันผลสอบหรือครอบคลุมทุกหัวข้อที่อาจออกสอบ

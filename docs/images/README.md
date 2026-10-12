# Visual Guidelines — AZ-802

ภาพประกอบของคอร์สเป็น **Mental Model**: ให้เห็นความสัมพันธ์หลัก แล้วเหลือพื้นที่ให้ผู้เรียนคิดต่อ ไม่ทำให้เหมือน Infographic หรือ Dashboard

## Visual rules

| Element | Rule |
|---|---|
| Palette | ขาว `#FFFFFF`, ดำ `#171717`, ฟ้า `#2563EB` |
| Accent | ใช้สีฟ้าเฉพาะ 1 เส้นทางหรือ 1 แนวคิดสำคัญในภาพ |
| Font | `Segoe UI, Arial, sans-serif` (ใช้ fallback ตามระบบ ไม่เก็บไฟล์ฟอนต์ใน Repo) |
| Font size | **สูงสุด 16px** รวมชื่อภาพ |
| Font weight | 400 (regular) และ 600 (semibold) |
| Shape | กรอบสี่เหลี่ยมมุมมน **5px** เป็นค่าหลัก; อนุญาต 3–7px |
| Lines | บางประมาณ 1.2–1.4px; เส้นประใช้เฉพาะความสัมพันธ์แบบไม่ตรงหรือ Boundary |
| Canvas | SVG (ขนาดปรับตามจำนวน Roles ที่ต้องสื่อ), พื้นหลังขาว, เว้นพื้นที่ว่างอย่างตั้งใจ |
| Content | หนึ่งภาพต่อหนึ่งแนวคิด; สำหรับ Topology ให้แสดง Logical Roles และแยกภาพใหญ่/ภาพเจาะลึก |

### ควรหลีกเลี่ยง

- Cards จำนวนมาก, กรอบตกแต่ง, เงา, Gradient, Icons และ Pill Badges
- สีเพื่อความสวยงามที่ไม่ได้มีความหมายทางเทคนิค
- คำอธิบายยาว ๆ ภายในภาพ
- ภาพเลียนแบบ Screenshot หรือ Azure Portal โดยไม่ได้ตรวจสอบ UI จริง

ภาพเป็น SVG ที่แก้ข้อความ เส้น รูปร่าง และสีได้โดยตรง และฝังใน Markdown ผ่าน Relative Path

## Diagram index

- [Track 1 — Complete logical server roles](lab-architecture.svg)
- [Track 2 — Complete hybrid architecture](advanced-track-architecture.svg)
- [Track 2 — S2D dependencies](advanced-s2d-cluster.svg)
- [01 — Active Directory](lab-01-ad-ds.svg)
- [02 — GPO and Windows LAPS](lab-02-gpo-laps.svg)
- [03 — DNS and DHCP](lab-03-dns-dhcp.svg)
- [04 — File Services](lab-04-file-services.svg)
- [05 — Hyper-V](lab-05-hyper-v.svg)
- [06 — Azure Arc](lab-06-azure-arc.svg)
- [07 — Monitoring](lab-07-monitoring.svg)
- [Final Challenge](final-challenge.svg)

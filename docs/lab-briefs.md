# Track 1 — Lab Topics

โจทย์ที่ผู้เรียนจะได้ฝึกใน Workshop (09:00–17:00) โดยใช้ระบบเดียวกันตั้งแต่ต้นจนจบ รายละเอียดแบบ Step-by-step จะใช้ในเอกสารประกอบการเรียนของผู้ลงทะเบียน

## Lab 01 — Active Directory

![Lab 01 — Active Directory](images/lab-01-ad-ds.svg)

**โจทย์:** เพิ่ม Domain Controller และตรวจว่า Directory พร้อมให้บริการ

**ลงมือทำ:** Promote Additional DC, ตรวจ Replication/DNS/SYSVOL และ FSMO Roles

**Expected Outcome:** DC ที่เพิ่ม Healthy และ AD Replication ตรวจสอบได้

## Lab 02 — Group Policy & Windows LAPS

![Lab 02 — GPO / Windows LAPS](images/lab-02-gpo-laps.svg)

**โจทย์:** กำหนด Policy และควบคุม Local Administrator Password อย่างปลอดภัย

**ลงมือทำ:** OU/GPO, Windows LAPS และตรวจผลจาก Windows Client

**Expected Outcome:** GPO Applied และ LAPS Backup/Permission ทำงานตามที่ออกแบบ

## Lab 03 — DNS & DHCP

![Lab 03 — DNS / DHCP](images/lab-03-dns-dhcp.svg)

**โจทย์:** ให้ Client ได้ IP Configuration ถูกต้องและติดต่อบริการด้วยชื่อได้

**ลงมือทำ:** DNS Records, DHCP Scope/Options/Reservation และ Name Resolution Tests

**Expected Outcome:** Client ได้ IP และ Resolve ชื่อ Server ได้ถูกต้อง

## Lab 04 — Secure File Services

![Lab 04 — File Services](images/lab-04-file-services.svg)

**โจทย์:** เปิด File Share ให้หลายฝ่ายใช้งานโดยกำหนดสิทธิ์อย่างเหมาะสม

**ลงมือทำ:** SMB Share, Share Permissions, NTFS Permissions และอาจเพิ่ม FSRM ตามเวลา

**Expected Outcome:** ผู้ใช้ที่มีและไม่มีสิทธิ์ได้รับผลการเข้าถึงตรงตาม Requirement

## Lab 05 — Hyper-V (Conditional)

![Lab 05 — Hyper-V](images/lab-05-hyper-v.svg)

**โจทย์:** เรียนรู้ Virtual Switch และ Recovery Point ของ VM

**ลงมือทำ:** Virtual Switch และ Checkpoint/Restore กับ Test VM ตามความพร้อมของ Environment

**Expected Outcome:** ตรวจ Network ของ VM และเข้าใจข้อจำกัดของ Checkpoint เทียบกับ Backup

## Lab 06 — Azure Arc

![Lab 06 — Azure Arc](images/lab-06-azure-arc.svg)

**โจทย์:** บริหาร On-premises Windows Server ผ่าน Azure

**ลงมือทำ:** Azure Arc Onboarding และ Update Manager Assessment

**Expected Outcome:** Server เชื่อมต่อ Azure Arc ได้ และตรวจ Update Status ได้

## Lab 07 — Monitoring & Diagnostics

![Lab 07 — Monitoring](images/lab-07-monitoring.svg)

**โจทย์:** ใช้หลักฐานจากระบบเพื่อหาสาเหตุปัญหา

**ลงมือทำ:** Event Viewer, Performance Monitor และ Diagnostic Commands

**Expected Outcome:** อธิบายอาการและผลตรวจจาก Logs/Commands ได้

## Final Troubleshooting Challenge

![Final Challenge](images/final-challenge.svg)

รับ Incident Scenario ของบริษัทสมมติแล้วใช้ข้อมูลที่ตรวจพบเพื่อสรุป Root Cause และ Validate ผลหลังแก้ไข

**Expected Outcome:** ระบุ Symptoms, Evidence, Fix และผลทดสอบหลังแก้ได้อย่างชัดเจน

---

[ตาราง Workshop](workshop-plan.md) · [Course Outline](course-outline.md) · [ค่าเรียนและ FAQ](pricing-and-faq.md)

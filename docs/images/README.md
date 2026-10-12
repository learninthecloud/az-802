# Visual Guidelines

ภาพประกอบของคอร์ส AZ-802 เป็น **mental model** ไม่ใช่ภาพตกแต่งหรือ Screenshot ของ UI

## Style

- White background, black/gray lines and text. No accent colors, gradients, shadows, decorative icons, or pill badges.
- Typeface: **Segoe UI** with system sans-serif fallback. Do not commit font files.
- 1–2 line weights maximum. Thin connections, simple rectangles, no oversized cards.
- Use the fewest elements that still explain the concept accurately.
- Prefer a single question per image: **What interacts with what?** or **How does this process work?**
- Clearly distinguish a direct interaction, bidirectional exchange, and conditional/indirect path.
- Text labels should be short and technically precise.
- SVG sources are editable and referenced by relative paths in Markdown.
- Keep diagrams 960 × 500 with enough margins for rendering on GitHub.
- Avoid trying to reproduce Azure Portal/Windows console views from memory; use a validated actual screenshot only if a UI walkthrough specifically requires one.

## Diagrams

- [Lab topology](lab-architecture.svg)
- [01 — Active Directory](lab-01-ad-ds.svg)
- [02 — GPO and Windows LAPS](lab-02-gpo-laps.svg)
- [03 — DNS and DHCP](lab-03-dns-dhcp.svg)
- [04 — Secure File Services](lab-04-file-services.svg)
- [05 — Hyper-V](lab-05-hyper-v.svg)
- [06 — Azure Arc](lab-06-azure-arc.svg)
- [07 — Monitoring](lab-07-monitoring.svg)
- [Final challenge](final-challenge.svg)

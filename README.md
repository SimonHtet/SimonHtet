# Hi, I'm Simon 👋

Manufacturing Systems Engineer at DairyPlus Co., Ltd. — self-taught across PLC integration, SQL Server, Python pipelines, and Power BI. Transitioning into data engineering and manufacturing IT.

---

## What I've Built

### 🏭 Smart Factory Platform
Built in-house after a vendor MES was quoted at ฿3M+ — the purchase was never needed. Python event pipeline for 23 Tetra Pak filler machines across 3 dairy production plants; production-operations core delivered in 6 months against an 18-month vendor timeline.

- Eliminates SQL Server trigger race conditions that blocked PLC writes under concurrent load
- Polls machine state at 1-second intervals, routes step transitions to event handlers with in-memory cooldowns
- **Reel → pallet recall traceability**: reverse-maps any finished pallet back to the supplier reel that fed it — and every other pallet that reel touched. Built around recall safety, deliberately choosing a method with bounded, predictable error over one that could fail silently
- **Downtime attribution / data integrity**: isolates upstream-line stalls from the filler's own downtime via PLC signal edge-detection, so efficiency KPIs reflect each machine's true performance instead of blaming it for an idle feed
- Data flows from multiple sources: PLC signals, SQL Server, and 16+ Budibase low-code apps (100+ daily active users) built in-house for production floor operations
- Designed layered data flows separating raw machine signals, event processing, and KPI reporting for manufacturing analytics
- Power BI dashboard tracking efficiency, waste%, and yield — reviewed weekly at director level
- Predictive maintenance prototype: Random Forest classifier (scikit-learn) scoring breakdown risk from running hours, temperature, and vibration — same signals the live pipeline collects
- *Jarvis for the Factory Floor* (Databricks hackathon): GenAI assistant answering natural-language questions over production data
- Formalized into the company's official Digital Transformation SOP (ISO/IEC 27001 aligned), approved at management level

→ *Private repo (live employer system, IP-protected) — architecture walkthrough available on request*

### 🏨 Staywise — Hotel PMS (SaaS)
Property-management system for boutique hotels — Next.js 14, Supabase/Postgres via Prisma, deployed on Vercel. 3-step check-in, folios & group billing with checkout settlement enforcement, night audit, multi-currency, role-based access, PDPA-compliant guest handling.

→ [Repo](https://github.com/SimonHtet/Simon) · live demo available on request

---

## Stack

```
Data & Backend    Python · SQL Server · PostgreSQL · pyodbc · Prisma
Frontend          Next.js · React · TypeScript · JavaScript · Tailwind
Low-Code          Budibase (16+ apps, 100+ daily active users)
BI & Analytics    Power BI · DAX · scikit-learn
Integration       PLC · WMS · SAP · REST APIs
DevOps            Vercel · Git · GitHub
```

---

## Currently

- 📍 Bangkok, Thailand
- 🎯 Looking for Data Engineering / MES / Manufacturing IT roles in Bangkok
- 🌱 Building Python and cloud skills alongside production work
- 📚 Expanding skills in pipeline orchestration, cloud platforms, and scalable data architecture

---

*Open to opportunities at manufacturing, FMCG, and tech companies in Bangkok.*

# Hi, I'm Simon 👋

**Manufacturing AI & Data Engineer** — building production-scale data platforms.

Currently Manufacturing Systems Engineer at DairyPlus Co., Ltd. — self-taught across PLC integration, SQL Server, Python pipelines, machine learning, and Power BI. Transitioning into data engineering and manufacturing IT.

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

→ [Repo](https://github.com/SimonHtet/staywise) · live demo available on request

---

## Repositories

| Repo | What it is |
|------|------------|
| 🏭 `smart-factory-platform` 🔒 | Flagship — Python event pipeline + SQL trigger engine + dbt + Power BI for 23 filler machines across 3 plants. Private (live employer system); architecture walkthrough on request |
| 🏨 [`staywise`](https://github.com/SimonHtet/staywise) | Staywise — hotel PMS SaaS. Next.js 14, Prisma, Supabase/Postgres, NextAuth, Vercel |
| 🚛 `fleet-planning` 🔒 | Continuous dock-timeline planner — SAP + WMS → auto dock assignment across 16 docks with variable durations and carton caps. Private (employer system) |
| 🥛 `UHT-Work` 🔒 | Offline-first app migration prototype for UHT filling operations. Private (employer system) |
| 🔧 [`preventive-maintenance-tracker`](https://github.com/SimonHtet/preventive-maintenance-tracker) | Mobile-friendly preventive maintenance tracker — photo uploads, signatures, PDF reporting (React + Vite) |
| 📊 [`hotel-analysis`](https://github.com/SimonHtet/hotel-analysis) | Hotel data analysis dashboard — Next.js, Prisma, Tailwind |
| 📓 `experiments` 🔒 | Scratch space — prototypes and notebook experiments. Private |
| 👋 [`SimonHtet`](https://github.com/SimonHtet/SimonHtet) | This profile |

---

## Stack

```
Data & Backend    Python · SQL Server · PostgreSQL · pyodbc · Prisma · dbt
Frontend          Next.js · React · TypeScript · JavaScript · Tailwind
Low-Code          Budibase (16+ apps, 100+ daily active users)
ML & Analytics    Power BI · DAX · scikit-learn · pandas
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

## Lessons Learned

Things production systems taught me that tutorials didn't:

- **Instrument before you theorize.** When PLC counters kept turning up NULL, no amount of reading the trigger code found it. A write-audit trap on the table caught the real culprit in days: a second writer (a low-code app doing full-row saves) silently overwriting machine-owned columns.
- **Guard system-owned data at the database layer.** Low-code apps are great for operator UIs, but the database is the last line of defense — a guard trigger that blocks 0/NULL regressions on PLC-owned columns turned a recurring silent corruption into an impossible one.
- **For recall traceability, a bounded predictable error beats a silent catastrophic one.** I chose supplier-declared counts (monotonic by construction, small bounded error) over the more precise live counter (which resets mid-run — one missed reset points a recall at the wrong product).
- **Never rewrite what production depends on.** The event trigger evolved V3 → V6 with each version strictly additive — every KPI that worked yesterday still works today, and any version can be diffed against the last.
- **Ship a package, not a notebook.** Production Python means a `src/` layout, separated config, and something a reviewer can run end-to-end — a notebook proves the idea, a package proves you can operate it.
- **Governance is part of engineering.** Getting the platform formalized into an approved SOP (ISO/IEC 27001 aligned) mattered as much as the code — it's what turns a side project into company infrastructure.

---

*Open to opportunities at manufacturing, FMCG, and tech companies in Bangkok.*

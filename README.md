<div align="center">

# Kiveshan Naidoo

**Backend &amp; Cloud Engineer** &nbsp;·&nbsp; AWS &nbsp;·&nbsp; Node.js &nbsp;·&nbsp; TypeScript &nbsp;·&nbsp; PostgreSQL

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-kiveshannaidoo-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)
&nbsp;
[![Email](https://img.shields.io/badge/Email-kiveshannaidoo9%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:kiveshannaidoo9@gmail.com)
&nbsp;
![Location](https://img.shields.io/badge/Durban-South%20Africa-4B5563?style=flat-square)
&nbsp;
![Remote](https://img.shields.io/badge/Open%20to-Remote%20globally-1a7f37?style=flat-square)

</div>

<br/>

Backend and cloud engineer with two years of production experience building systems for external paying clients across logistics, healthcare, finance, and the public sector.

My ELT pipeline has run unattended in production since August 2025, processing **~750,000 records per nightly run**. I've delivered four production systems end-to-end — architecture, AWS infrastructure, CI/CD, and post-launch support — without a separate DevOps function. On the logistics platform I lead a team of five.

**Currently building:**

- **WhizzFleet** — a greenfield multi-tenant fleet management platform for trucking and logistics clients. TypeScript monorepo, Express, Prisma, PostgreSQL. Multi-tenancy designed in from the first commit rather than retrofitted.
- **Neo4j knowledge graph layer** over the government-sector data lakehouse, modelling sector skills relationships for multi-hop traversal queries that relational multi-joins handle badly.

**Architecture case studies** — write-ups of the design decisions and trade-offs behind three client-confidential production systems, with no client-identifying detail: [data lakehouse](https://github.com/Kiveshan/data-lakehouse-case-study) &nbsp;·&nbsp; [logistics platform](https://github.com/Kiveshan/logistics-platform-casestudy) &nbsp;·&nbsp; [pharmacy delivery](https://github.com/Kiveshan/pharmacy-delivery-casestudy)

<br/>

## Stack

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=for-the-badge&logo=neo4j&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

</div>

<br/>

**AWS services I've run in production**

`Lambda` &nbsp; `Step Functions` &nbsp; `Glue (PySpark)` &nbsp; `DMS` &nbsp; `S3` &nbsp; `RDS` &nbsp; `EventBridge` &nbsp; `Elastic Beanstalk` &nbsp; `CloudWatch` &nbsp; `IAM` &nbsp; `Location Service` &nbsp; `Cost Explorer`

**Beyond AWS**

- **Backend** — Node.js, Express, TypeScript, REST API design, OAuth 2.0, JWT auth
- **Data** — PostgreSQL, Prisma, Neo4j, PySpark, Kimball dimensional modelling, SCD Type 2
- **Delivery** — GitHub Actions CI/CD, least-privilege IAM, multi-environment release management
- **Frontend** — React, Vite, Chart.js

<br/>

## Selected Work

### [AWS Data Lakehouse &amp; Analytics Platform](https://github.com/Kiveshan/data-lakehouse-case-study)

> End-to-end ELT pipeline for a government-sector skills planning client. Azure SQL source → S3-backed raw, curated, and serving layers.

`AWS Glue (PySpark)` &nbsp; `DMS` &nbsp; `Step Functions` &nbsp; `Apache Iceberg` &nbsp; `S3` &nbsp; `RDS` &nbsp; `Neo4j`

- ~750,000 records ingested per nightly run, unattended in production since August 2025
- 400 entities modelled in a Kimball-compliant dimensional schema with SCD Type 2 on Apache Iceberg, enabling point-in-time historical analysis across the full dataset
- PySpark transforms in Glue applying schema normalisation, data-quality validation, and deduplication before promotion from raw to curated
- Two-level Step Functions design separating ingestion from transformation, with exponential backoff, retry limits, and SNS failure alerting — so a broken run surfaces rather than silently serving stale data

<br/>

### [Trucking Logistics Management System](https://github.com/Kiveshan/logistics-platform-casestudy)

> Replaced a client's entirely paper-based operation. Led a 5-person team from requirements through to production.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `React` &nbsp; `Lambda` &nbsp; `EventBridge`

- Re-architected from single-tenant to multi-tenant SaaS — row-level data isolation via `company_id` across all tenant-scoped tables, middleware-enforced tenant context on every authenticated request, and a redesigned auth layer. **Live with 4 paying clients.**
- Statement aging recomputed live against outstanding items rather than carried forward from last month's closing balance, so every statement is a true point-in-time snapshot instead of an accumulated ledger
- Driver rates versioned with effective-date ranges, so historical invoices stay reproducible at whatever rate was in force when the leg actually ran
- Month-end statement generation triggered by EventBridge and Lambda rather than in-process cron, eliminating a 2-day manual finance process and decoupling the run from application uptime

<br/>

### [Pharmacy &amp; Delivery Management System](https://github.com/Kiveshan/pharmacy-delivery-casestudy)

> Driver-facing delivery module of a production pharmacy dispensing platform — route sequencing, live tracking against a metered provider, and proof of delivery over an unreliable network.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `Prisma` &nbsp; `AWS Location Service` &nbsp; `React`

- Closed a read-check-write race reachable through the offline queue by moving the condition into the update itself and letting the affected-row count decide the winner
- Ordered driver breadcrumbs by a server-assigned sequence rather than device timestamps, after unreliable device clocks produced traced paths that doubled back on themselves
- Cut metered geolocation spend with an address-hash geocode cache, per-leg routing in place of a distance matrix, and a write cadence that adapts to movement state — roughly 1,200 requests per driver-hour collapsed to one per flush window
- Durable client-side outbox (IndexedDB) so deliveries completed without signal replay in order, treating a 4xx as an answer to report and a network error as a condition to wait out

<br/>

### [Multi-Platform Financial Analytics Dashboard](https://github.com/Kiveshan/BizExecData)

> Unified revenue, expense, and P&amp;L reporting across three structurally different accounting providers.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `Prisma` &nbsp; `OAuth 2.0` &nbsp; `Chart.js`

- Integrated Xero, QuickBooks, and Sage via REST, normalising three incompatible P&amp;L report shapes into a single `{category, amount, date}` schema plus a common monthly calculation
- Three credential models handled on their own terms rather than forced into one abstraction — OAuth 2.0 with DB-persisted tokens and explicit refresh for QuickBooks, SDK-delegated OAuth for Xero, and AES-encrypted per-session credentials for Sage, whose reseller API offers only HTTP Basic auth
- Diff-based incremental extraction — three years back on first connect, one year on refresh, writing only where the incoming amount differs, so a re-run is close to a no-op
- Excel P&amp;L import pipeline as a fallback for clients without a supported accounting integration

<br/>

## Credentials

| | |
|:---|:---|
| **Bachelor of Information &amp; Communications Technology** — Cum Laude | Durban University of Technology · 2020–2023 |

<br/>

---

I document architecture decisions, not just implementations — including the ones I got wrong. Every case study above has a section on what I'd do differently. I don't hand off to a DevOps team; I am the DevOps function.

<div align="center">
<br/>

*Open to remote backend and cloud engineering roles globally.*

<br/>

[![Connect on LinkedIn](https://img.shields.io/badge/Connect%20on%20LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)

</div>

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
- **Public architecture case studies** for three client-confidential systems — write-ups of the design decisions and trade-offs, no client-identifying detail.

<br/>

## Stack

<div align="center">

[![Skills](https://skillicons.dev/icons?i=nodejs,ts,js,python,postgres,react,aws,neo4j,prisma,githubactions&theme=dark&perline=5)](https://skillicons.dev)

</div>

<br/>

<details>
<summary><strong>AWS services I've run in production</strong></summary>

<br/>

`Lambda` &nbsp; `Step Functions` &nbsp; `Glue (PySpark)` &nbsp; `DMS` &nbsp; `S3` &nbsp; `RDS` &nbsp; `EventBridge` &nbsp; `Elastic Beanstalk` &nbsp; `CloudWatch` &nbsp; `IAM` &nbsp; `Location Services` &nbsp; `Cost Explorer`

</details>

<details>
<summary><strong>Beyond AWS</strong></summary>

<br/>

**Backend** — Node.js, Express, TypeScript, REST API design, OAuth 2.0, JWT auth
**Data** — PostgreSQL, Prisma, Neo4j, PySpark, Kimball dimensional modelling, SCD Type 2
**Delivery** — GitHub Actions CI/CD, least-privilege IAM, multi-environment release management
**Frontend** — React, Vite, Chart.js

</details>

<br/>

## Selected Work

### AWS Data Lakehouse &amp; Analytics Platform
<!-- Add case study link here once the repo is public -->

> End-to-end ELT pipeline for a government-sector skills planning client. Azure SQL source → S3-backed raw, curated, and serving layers.

`AWS Glue (PySpark)` &nbsp; `DMS` &nbsp; `Step Functions` &nbsp; `S3` &nbsp; `RDS` &nbsp; `Neo4j` &nbsp; `Node.js`

- ~750,000 records ingested per nightly run, unattended in production since August 2025
- 400 entities modelled in a Kimball-compliant dimensional schema with SCD Type 2, enabling point-in-time historical analysis across the full dataset
- PySpark transforms in Glue applying schema normalisation, data-quality validation, and deduplication before promotion from raw to curated
- Step Functions orchestration with conditional branching and retry logic — automatic failure recovery across DMS, Glue, and downstream jobs with no manual intervention

<br/>

### Trucking Logistics Management System
<!-- Add case study link here once the repo is public -->

> Replaced a client's entirely paper-based operation. Led a 5-person team from requirements through to production.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `React` &nbsp; `Lambda` &nbsp; `EventBridge`

- Re-architected from single-tenant to multi-tenant SaaS — row-level data isolation via `company_id` across all tenant-scoped tables, middleware-enforced tenant context on every authenticated request, and a redesigned auth layer. **Live with 4 paying clients.**
- Lambda triggered by EventBridge automating month-end statement generation, eliminating a 2-day manual finance process
- Receivables aging report bucketing balances by overdue period, plus subcontractor commission reporting showing net margin per job

<br/>

### Pharmacy &amp; Delivery Management System
<!-- Add case study link here once the repo is public -->

> Prescription management, delivery route optimisation, and live driver tracking for a pharmacy operation.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `Prisma` &nbsp; `AWS S3` &nbsp; `AWS Location Services`

- Nearest-neighbour route heuristic (O(n²)) sequencing 20–50 daily delivery stops per driver, with a fixed-window override for time-constrained deliveries
- Chose 3-second polling over WebSockets for live driver tracking — materially simpler to operate at that update frequency — writing coordinates to PostgreSQL and rendering position on an AWS Location Services map
- Multi-layer prescription validation: dosage rules, controlled-substance checks, and patient record integrity, with S3-backed document archiving for regulatory compliance

<br/>

### Multi-Platform Financial Analytics Dashboard
<!-- Add repo link here once the secrets audit is complete -->

> Unified revenue, expense, and P&amp;L reporting across three structurally different accounting providers.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `Prisma` &nbsp; `OAuth 2.0` &nbsp; `Chart.js`

- Integrated Xero, QuickBooks, and Sage via REST, normalising three incompatible financial data models into a single reporting schema
- OAuth 2.0 flows for all three providers — token refresh cycles, secure token storage, per-provider scope configuration
- Excel P&amp;L import pipeline as a fallback for clients without a supported accounting integration

<br/>

## Credentials

| | |
|:---|:---|
| **Bachelor of Information &amp; Communications Technology** — Cum Laude | Durban University of Technology · 2020–2023 |

<br/>

---

I instrument production systems before I consider them done. I document architecture decisions, not just implementations. I don't hand off to a DevOps team — I am the DevOps function.

<div align="center">
<br/>

*Open to remote backend and cloud engineering roles globally.*

<br/>

[![Connect on LinkedIn](https://img.shields.io/badge/Connect%20on%20LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)

</div>

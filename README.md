# Kiveshan Naidoo

**Backend & Data Platform Engineer**  ·  AWS  ·  TypeScript/Node.js  ·  Python  ·  PostgreSQL  ·  Terraform

[![LinkedIn](https://img.shields.io/badge/LinkedIn-kiveshannaidoo-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)
![Email](https://img.shields.io/badge/Email-kiveshannaidoo9%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)
![Location](https://img.shields.io/badge/Durban-South%20Africa-4B5563?style=flat-square)

Backend engineer who builds data platforms end to end on AWS, from ingestion and modelling to the Terraform-managed infrastructure underneath. I've delivered five production systems for external paying clients across government, logistics, healthcare and finance, and I lead a five-person team, with no separate DevOps function behind us.

**Now:**

- **DHET data ingestion system** (live since August 2026, sole developer). National student and staff data for the Department of Higher Education and Training. Providers won't open their firewalls, so they run the extractor themselves and land their tables as Parquet in S3, using short-lived credentials from a FastAPI broker scoped to their own prefix. Table fingerprints before and after every read and atomic landing mean incomplete data is never published.
- **WhizzFleet**, a multi-tenant fleet management platform for trucking clients, live with its first paying client. TypeScript, Express, Prisma, PostgreSQL on ECS Fargate, all in Terraform. Multi-tenancy designed in from the first commit.

**Architecture case studies.** These are write-ups of the design decisions and trade-offs behind three production systems: [data lakehouse](https://github.com/Kiveshan/data-lakehouse-case-study)  ·  [logistics platform](https://github.com/Kiveshan/logistics-platform-casestudy)  ·  [pharmacy delivery](https://github.com/Kiveshan/pharmacy-delivery-casestudy)

## Stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white) ![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) ![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)

**AWS services I've run in production**

`S3`   `STS`   `IAM`   `Lambda`   `Step Functions`   `Glue (PySpark)`   `DMS`   `RDS`   `ECS Fargate`   `ALB`   `EventBridge`   `CloudWatch`   `SNS`   `Secrets Manager`   `Route 53`   `Location Service`

**Infrastructure as Code**

`Terraform`: remote state with native S3 locking (Terraform ≥1.11), no DynamoDB lock table

**Beyond AWS**

- **Backend:** TypeScript, Node.js, Express, Prisma, Python (FastAPI, Pydantic), REST API design, OAuth 2.0
- **Data:** PostgreSQL, SQL Server, Parquet (PyArrow), PySpark, Apache Iceberg, Kimball dimensional modelling, SCD Type 2
- **Testing:** pytest, testcontainers, mypy (strict), ruff
- **Delivery:** GitHub Actions CI/CD with OIDC, least-privilege IAM, multi-environment release management

## Selected Work

### DHET Data Ingestion System

> Ingestion layer for the Department of Higher Education and Training's national student and staff data. Live since August 2026, with a provider sending data every day. Sole developer. Code is not public.

`Python`   `FastAPI`   `Pydantic`   `SQL Server`   `PyArrow/Parquet`   `Docker`   `S3`   `STS`   `pytest`   `testcontainers`

- **Extractor runs on the provider's side.** Providers wouldn't open their firewalls, so the extractor runs inside their network and pushes out.
- **Credential broker.** No provider holds long-lived cloud keys. The broker issues short-lived STS credentials scoped to the provider's own S3 prefix, with rotation, revocation, rate limiting and a full audit trail.
- **Completeness guarantee.** Providers delete source rows after each run, so the system must never publish incomplete data. It takes table fingerprints before and after every read (a sum of checksums, since XOR would cancel out duplicate rows) and lands each batch atomically behind a `_SUCCESS` marker.
- **Testing against real dependencies.** Tests run against real SQL Server and storage containers rather than mocks, which caught a bug the mocks had missed.
- **Failure handling.** Each failure has its own exit code, so a provider's scheduler can tell "retry later" from "call someone".

### [AWS Data Lakehouse (MICT SETA)](https://github.com/Kiveshan/data-lakehouse-case-study)

> End-to-end ELT pipeline for the MICT SETA, provisioned entirely as Terraform-managed infrastructure. It ran unattended every night from August 2025 to August 2026, when the client stopped funding it.

`AWS Glue (PySpark)`   `DMS`   `Step Functions`   `Apache Iceberg`   `S3`   `RDS`   `Terraform`

- **Volume:** about 750,000 records a night, from a cross-cloud Azure MySQL source through DMS, Glue and Iceberg into an RDS PostgreSQL serving layer.
- **History and modelling:** full change history for 353 source tables with SCD Type 2. 47 of them were modelled into a Kimball star schema of 14 fact tables and 15 conformed dimensions.
- **Orchestration:** two Step Functions state machines and 9 Lambdas replaced a manually run chain of jobs, with exponential backoff, retry limits and SNS failure alerts.
- **Infrastructure:** all of it in Terraform, so the environment rebuilds from code rather than from console history.

### [Trucking Logistics Management System](https://github.com/Kiveshan/logistics-platform-casestudy)

> Replaced a client's entirely paper-based operation. I led a 5-person team from requirements through to production.

`TypeScript`   `Node.js`   `PostgreSQL`   `React`   `Lambda`   `EventBridge`

- **Multi-tenancy.** Re-architected from single-tenant to multi-tenant SaaS: row-level isolation via `company_id`, middleware-enforced tenant context on every authenticated request, and a redesigned auth layer. **Live with 4 paying clients.**
- **Statements.** Statement aging is recomputed live against outstanding items rather than carried forward, so every statement is a true point-in-time snapshot.
- **Historical rates.** Driver rates are versioned with effective-date ranges, so historical invoices stay reproducible.
- **Month-end automation.** EventBridge and Lambda generate statements at month end, replacing a 2-day manual finance process.

### [Pharmacy & Delivery Management System](https://github.com/Kiveshan/pharmacy-delivery-casestudy)

> The driver-facing delivery module of a production pharmacy dispensing platform.

`Node.js`   `PostgreSQL`   `Prisma`   `AWS Location Service`   `React`

- **Race condition.** Closed a read-check-write race reachable through the offline queue by moving the condition into the update itself. The affected-row count decides the winner, proved with 10 concurrent requests against one row.
- **Ordering.** Driver breadcrumbs are ordered by a server-assigned sequence rather than device timestamps.
- **Cost.** Metered geolocation spend was cut with a geocode cache, per-leg routing and a movement-aware write cadence.
- **Offline support.** A durable IndexedDB outbox lets deliveries completed without signal replay in order.

### [Multi-Platform Financial Analytics Dashboard](https://github.com/Kiveshan/BizExecData)

> Unified P&L reporting across Xero, QuickBooks and Sage.

`Node.js`   `PostgreSQL`   `Prisma`   `OAuth 2.0`

- **Normalisation.** Three incompatible P&L report shapes are normalised into a single schema.
- **Credentials.** Three credential models are handled on their own terms: OAuth 2.0 with refresh for QuickBooks, SDK-delegated OAuth for Xero, and encrypted per-session credentials for Sage.
- **Incremental sync.** Diff-based incremental extraction makes a re-run close to a no-op.

## Credentials

| | |
|:--|:--|
| **Bachelor of Information & Communications Technology**, Cum Laude | Durban University of Technology · 2020–2023 |

---

I document architecture decisions, not just implementations, including the ones I got wrong.

*Open to backend, platform, cloud and data engineering roles in Durban, Cape Town, Johannesburg or remote from South Africa.*

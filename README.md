<div align="center">

<h1>Kiveshan Naidoo</h1>

![Stack](https://readme-typing-svg.demolab.com?font=Geist+Mono&weight=400&size=14&duration=4000&pause=99999&color=6E7681&center=true&vCenter=true&repeat=false&width=680&height=28&lines=Backend+%26+Cloud+Engineer+%E2%80%94+AWS+%C2%B7+Node.js+%C2%B7+TypeScript+%C2%B7)

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-kiveshannaidoo-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)
&nbsp;
[![Email](https://img.shields.io/badge/Email-kiveshannaidoo9%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:kiveshannaidoo9@gmail.com)
&nbsp;
[![Remote](https://img.shields.io/badge/Open%20to-Remote%20globally-1a7f37?style=flat-square)](https://linkedin.com/in/kiveshannaidoo)

</div>

<br/>

Backend and cloud engineer with 1.5 years of production experience. My ELT pipeline has processed **750,000+ records per nightly run, unattended, since August 2025.** I've delivered 4 production systems for paying clients across logistics, finance, and healthcare — owning architecture decisions, AWS infrastructure, CI/CD, and post-launch support without a separate DevOps function.

**Currently:**
- Re-architecting a logistics platform from single-tenant to multi-tenant SaaS — row-level isolation, redesigned auth, billing integration
- Extending a government sector data lakehouse with a Neo4j knowledge graph for multi-hop traversal queries
- Migrating existing deployments from Elastic Beanstalk to ECS Fargate, provisioned via Terraform

<br/>

## Stack

<div align="center">

[![Skills](https://skillicons.dev/icons?i=nodejs,ts,js,python,postgres,react,aws,terraform,docker,neo4j,prisma,githubactions&theme=dark&perline=6)](https://skillicons.dev)

</div>

<br/>

<details>
<summary><strong>AWS services used in production</strong></summary>
<br/>

`Lambda` &nbsp; `Step Functions` &nbsp; `Glue (PySpark)` &nbsp; `DMS` &nbsp; `S3` &nbsp; `RDS` &nbsp; `ECS Fargate` &nbsp; `ECR` &nbsp; `EventBridge` &nbsp; `CloudWatch` &nbsp; `IAM` &nbsp; `Location Services` &nbsp; `SNS` &nbsp; `SQS` &nbsp; `Cost Explorer`

<br/>
</details>

<br/>

## Selected Work

### [AWS Data Lakehouse & Analytics Platform](#)
> End-to-end ELT pipeline for a government sector skills planning client — Azure SQL source → S3-backed raw, curated, and serving layers.

`AWS Glue (PySpark)` &nbsp; `DMS` &nbsp; `Step Functions` &nbsp; `S3` &nbsp; `RDS` &nbsp; `Neo4j` &nbsp; `Node.js`

- 750,000+ records ingested per nightly run, unattended since August 2025
- 400+ entities modelled in a Kimball-compliant dimensional schema with SCD Type 2; full point-in-time historical analysis
- Step Functions orchestration with conditional branching and automatic failure recovery across DMS, Glue, and downstream jobs
- Extending with a Neo4j knowledge graph for multi-hop entity traversal — replacing costly multi-join relational queries

<br/>

### [Trucking Logistics Management System](#)
> Replaced a fully paper-based client operation. Led a 5-person team from requirements through production.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `React` &nbsp; `Lambda` &nbsp; `EventBridge`

- Lambda + EventBridge automated month-end statement generation — eliminated a 2-day manual finance process
- Receivables aging report and subcontractor commission reporting built from scratch
- Currently re-architecting for multi-tenancy: row-level isolation with `company_id` across all tenant-scoped tables, middleware-enforced tenant context on every authenticated request

<br/>

### [Pharmacy & Delivery Management System](#)
> Prescription management, delivery route optimisation, and live driver tracking for a pharmacy operation.

`Node.js` &nbsp; `PostgreSQL` &nbsp; `Prisma` &nbsp; `AWS S3` &nbsp; `AWS Location Services`

- Nearest-neighbour route heuristic (O(n²)) sequencing 20–50 daily delivery stops per driver, with time-window overrides for priority runs
- Live driver tracking via 3-second polling architecture → PostgreSQL → AWS Location Services map
- Multi-layer prescription validation: dosage rules, controlled substance checks, and S3-backed document archiving for regulatory compliance

<br/>

## GitHub Stats

<div align="center">

![GitHub Streak](https://streak-stats.demolab.com?user=Kiveshan&theme=github-dark-blue&hide_border=true&date_format=j%20M%5B%20Y%5D)

</div>

<br/>

## Credentials

| | |
|:---|:---|
| 🎓 **BCT Information & Communications Technology — Cum Laude** | Durban University of Technology · 2020–2023 |

<br/>

---

I write infrastructure as code. I instrument production systems before I consider them done. I document architecture decisions, not just implementations. I don't hand off to a DevOps team — I am the DevOps function.

*Open to remote backend and cloud engineering roles globally.*

<div align="center">
<br/>

[![Connect on LinkedIn](https://img.shields.io/badge/Connect%20on%20LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/kiveshannaidoo)

</div>

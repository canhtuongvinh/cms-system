# Datastore Solution Overview

The CMS handles structured complaints, flexible claim guidelines, and large binary attachments. Three storage models fit these needs:
- Relational storage for complaints.
- Document storage for guidelines.
- Blob storage for attachments.

## Considered Data Store Approaches

### Relational
Relational storage fits structured complaint records. Complaints follow predictable fields, clear relationships, and strict audit requirements. Each record links to tenants, consumers, staff users, workflow actions, and logs. These links benefit from strong consistency.

Reasons to choose relational storage for complaints:

- Complaints have stable schema. Case IDs, timestamps, status, assigned staff, tenant ID.
- Regulators expect reliable audit trails and consistent updates.
- Workflows need linkages between complaints, notes, actions, and users.
- SQL fits reporting needs. Tenants run performance summaries and SLA analyses.
- Indexes support high volume. This suits global scale with millions of consumers.

Relational storage supports the CMS goals for availability, scalability, and fault tolerance.

[ADR-007: Select PostgreSQL for Core Complaint Data](https://github.com/canhtuongvinh/cms-system/blob/772b6df49aeceb8bfbdfd5a2eaa02589d10504af/ADRs/ADR-007-select-postgreSQL-for-core-complaint-data.md)

<img src="../assets/images/relational.png" width="150" height="150"/>

### Document

Document storage fits with uneven guidance data. Claim guidelines differ across tenants. Some have short text. Others contain nested instructions, conditional rules, or long explanations.

Reasons to choose document storage for guidelines:

- Structure varies. Fields differ across tenants or guideline types.
- Guidelines change often. Updates do not require schema migrations.
- Missing fields are omitted. This avoids sparse relational tables.
- Data is read frequently and updated regularly.
- Guidelines do not need complex joins or SQL-style reporting.

Document storage keeps guidelines flexible and simple to maintain.

[ADR-005: Adopt a NoSQL Database for Procedures](https://github.com/canhtuongvinh/cms-system/blob/4732f4f7c060b0243ae2fb820e112e8113270a71/ADRs/ADR-005-adopt-nosql-database-for-procedures.md)

<img src="../assets/images/diagram.png" width="150" height="150"/>

### Blob

Binary Large Object storage is optimised for unstructured binary files that are large in size, e.g. videos and images. Consumers upload photos, PDFs, audio files, or scanned documents when filing complaints. Staff upload supporting evidence. These files must be stored securely and delivered efficiently.

Blob storage isolates heavy file content from core complaint data and reduces database load.

<img src="../assets/images/binary-data.png" width="150" height="150"/>

### Graph

A graph store fits highly connected data with heavy pattern analysis. The CMS does not have this type of workload for its core functions.

<img src="../assets/images/nodes.png" width="150" height="150"/>

## Summary
Use relational storage for complaint data due to its structured nature and strong integrity needs. Use document storage for claim guidelines due to their flexible shape. Use blob storage for attachments due to their size and unstructured form. This mix fits the CMS performance, maintainability, and scalability goals.

[Above icons made by: relational: [ultimatearm](https://www.flaticon.com/authors/ultimatearm), diagram: [Becris](https://www.flaticon.com/authors/becris), binary-data: [Juicy-Fish](https://www.flaticon.com/authors/juicy-fish)

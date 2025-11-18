# ADR-005: Adopt a NoSQL Store for Procedures

## Context

Procedures data is flexible and does not follow a fixed structure. Guidance entries include long text, nested steps, and tags. These fields change often. The CMS needs a store that handles irregular content without complex migrations. The Procedures data does not require heavy auditing or analytical queries.

## Decision

Use MongoDB for the Procedures database. Each guidance entry is stored as a document. The document model supports variable fields, nested data, and text-heavy content. MongoDB spreads data across servers with ease and omits NULL fields, which improves read and write performance for irregular datasets.

## Consequences

**Positive:**

- Simple storage for variable fields.
- Fast handling of large text and nested data.
- Improved performance due to omitted NULL fields.
- Easy horizontal distribution.

**Negative:**

- Weaker support for complex analytical queries.

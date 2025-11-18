# Select Microservices architecture design

## Status

Confirmed

## Context

[Analysis of the architecture characteristics](https://github.com/canhtuongvinh/cms-system/blob/83cf945c54b5b0655fd3c5fc5a93c0d3dc56463c/SolutionBackground/ArchitecturePatterns.md)

[Analysis of the architecture characteristics](../2.SolutionBackground/ArchitecturePatterns.md) required of the system and the possible architecture styles concluded that an event-driven architecture would suit the system, with less trade-offs than other options.

## Decision

Use an event-driven architecture for the backend of the system.

## Consequences

**Positive:**

- Four of seven characteristics score highly.

**Negative:**

- Interoperability needs to be mitigated.

**Risks:**

- Interoperability and configurability may still be high trade-offs after mitigation.

---

[> Home](../README.md)    [> ADRs](README.md)

# ADR-002: Cost Not Selected as a Driving Characteristic

## Context

The CMS platform is intended for large-scale enterprise clients such as national banks, telecom providers, insurance firms, and multinational organisations. These companies typically operate with millions of customers, strict regulatory requirements, and high expectations of reliability and performance.

In such environments, **cost efficiency is not the primary decision driver**. Instead, these organisations prioritise system qualities such as **scalability, reliability, security, integration capability, maintainability**. A budget system that compromises these qualities introduces unacceptable business risk, operational delays, and potential reputational damage.

Cost remains relevant from a business perspective, but **it is not a core architectural driver** for decision-making in this project.

Refer to:
[Analysis of the architecture characteristics](https://github.com/canhtuongvinh/cms-system/blob/83cf945c54b5b0655fd3c5fc5a93c0d3dc56463c/SolutionBackground/ArchitecturePatterns.md)

## Decision

Cost will *not* be selected as a driving characteristic in the architectural design of the CMS. The architecture will prioritise **quality attributes** such as scalability, performance, fault tolerance, extensibility, and maintainability, even when this requires higher implementation or infrastructure cost.

## Consequences

By deprioritising cost as a driving characteristic, the architecture can be designed around what enterprise clients actually value: **robustness, long-term stability, and global-scale capability**.

### Pros

-   **Higher Quality Product**: Enables the selection of architectural patterns (e.g., SOA, distributed components, high-availability
    deployments) that meet enterprise expectations.
-   **Better Fit for Large Tenants**: Banks and telecoms favour systems that can scale to tens of millions of users globally, where reliability matters more than cost.
-   **Long-Term Maintainability**: Prioritising maintainable and modular solutions reduces technical debt and operational risk over time.
-   **Supports Future Growth**: Trading upfront cost for scalable infrastructure prevents expensive redesigns when the system grows.

### Cons

-   **Higher Initial Cost**: The platform may require more expensive infrastructure (e.g., scalable databases, distributed services, clusters).
-   **More Complex Architecture**: Architectures optimised for quality attributes can introduce increased system complexity.
-   **Longer Development Time**: Best-practice patterns and high-quality components may take longer to implement compared to cheaper solutions.

# Overall Architecture Style Analysis

## Identified Key Architectural Characteristics

Selecting the appropriate architectural characteristics is a key step that shapes the overall system design and its data flows. By evaluating these characteristics early, we can identify the most suitable software and hardware components needed to meet the system’s requirements. This approach ensures the solution functions correctly while remaining scalable, maintainable, and high-performing. From the analysis and requirements, the following three characteristics have been chosen as the most important:
The key architectural characteristics identified for the Complaint Management System (CMS) guide the selection of the overall architecture style.  
The top three are shown in **bold** and with a ^.

- **Availability ^**
- **Scalability ^**
- **Security ^**
- Fault Tolerance
- Performance
- Extensibility
- Configurability
- Interoperability

## Architecture Capabilities Comparison

The characteristics are highlighted below in the comparison matrix, with a particular focus on the three driving characteristics:  
**availability**, **scalability**, and **security**, all of which are critical for a multi-tenant CMS expected to support global-scale enterprises and millions of users.

![Alt text](
/assets/architectural-styles-marked.png "Optional Title")

[comparison matrix from DeveloperToArchitect.com]

## Architecture Capabilities Analysis

Using the matrix, three feasible architecture style candidates were identified:

### 1. Microservices  
### 2. Service-Oriented Architecture (SOA)  
### 3. Event-Driven Architecture (EDA)

Below is the comparative analysis for each, following the same structure and level of detail as the reference example.

---

# Microservices

| Pros | Cons | Mitigations |
|------|------|-------------|
| **Scores extremely high on scalability**, essential for a CMS with tenants that may have tens of millions of customers. | Lower simplicity due to distributed components. | Keep a bounded set of domain services; use Kubernetes + full CI/CD automation. |
| **High availability and fault-tolerance**, meaning an outage in Notifications does not impact Complaint Intake or User Authentication. | Requires separated or isolated databases per service. | Logical separation through schemas + strong tenant isolation policies. |
| Strong evolvability, allowing the CMS to add future products (AI agent, chatbot, analytics engine) with minimal disruption. | Higher infrastructure cost. | Cost is *not* a driving characteristic; enterprises favour resilience over savings. |
| Excellent domain partitioning. Complaints, Users, Guidelines, Notifications, Integrations, Reporting map naturally to microservices. | Cross-service workflows more complex. | Use asynchronous patterns and workflow orchestrators (e.g., Temporal). |
| High deployability, services can update independently with zero downtime. | Requires more DevOps maturity. | Invest in automation, observability, and API versioning discipline. |

---

# Service-Oriented Architecture (SOA)

| Pros | Cons | Mitigations |
|------|------|-------------|
| Higher configurability and strong integration capability, beneficial for linking CRM, email, SMS, and telecom channels. | **Lower scalability** compared to microservices; ESB patterns become bottlenecks. | Vertical scaling helps initially but lacks long-term elasticity. |
| Centralised governance and consistency. | **Lower availability**, as shared services or ESB failures cascade. | Add redundancy, but this increases complexity and cost. |
| Straightforward workflow modelling. | **Lower performance** under high concurrency workloads. | Caching helps but cannot match granular microservice scaling. |
| Familiar to large organisations. | ESB introduces a single point of failure and slows delivery. | Distributed brokers add complexity without the benefits of microservices. |

---

# Event-Driven Architecture (EDA)

| Pros | Cons | Mitigations |
|------|------|-------------|
| **Scores very high on scalability and elasticity**, ideal for high-volume events like notifications, audit trails, or real-time updates. | Low configurability and abstraction (per matrix), which conflicts with CMS customisation needs. | Keep EDA for async messaging only; not overall system structure. |
| Excellent fault tolerance, components fail independently. | **Not strong in domain partitioning**, making ownership boundaries unclear. | Combine EDA *with* microservices (events as integration). |
| High performance for asynchronous workloads. | Complex debugging and eventual consistency issues. | Use event tracing, structured logging, and idempotent consumers. |
| Useful for push-based updates (email/SMS/chat events). | Poor workflow support if used as the primary architecture. | Pair with orchestrators or retain request-response flows for core flows. |

---

## Conclusion

All three architecture styles score well in specific areas, but their trade-offs differ significantly.

- **SOA** excels at integration and governance but scores poorly in scalability, availability, and performance, all top drivers for the CMS.
- **Event-Driven** excels at asynchronous messaging but does *not* meet domain partitioning, configurability, or workflow requirements for the core business model.
- **Microservices** aligns most closely with the CMS’s highest-priority characteristics:

### ✔ Highest scalability  
### ✔ Highest availability  
### ✔ Strong isolation for security and tenant separation  
### ✔ Supports independent evolvability  
### ✔ Ideal for global deployment and enterprise SLAs  

While Microservices introduce additional operational complexity, this is an acceptable and manageable trade-off for the CMS domain and its target enterprise market.

---

# Decision

ADR: **[003 We-will-use-a-microservices-architecture](../4.ADRs/003-We-will-use-a-microservices-architecture.md)**


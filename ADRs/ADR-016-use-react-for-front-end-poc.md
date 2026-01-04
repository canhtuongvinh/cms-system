# ADR-016: Use React for front-end POC

## Context

The CMS proof of concept needs a front end that demonstrates the full complaint lifecycle. This includes role based views for Consumer, Help Desk Agent, Support Person, Manager, and Admin. The interface needs rapid iteration during development, a clear component structure, and basic accessibility support. The front end also needs clean integration with the API layer and alignment with future expansion into a production grade system.

## Decision

Use ReactJS for the CMS front end proof of concept. Build the interface using reusable components and route users to role specific screens. Connect components to backend REST endpoints through a simple service layer. This choice keeps focus on validating user flows, API design, and architectural decisions rather than UI framework complexity.

## Consequences

Positive:
- Fast iteration during proof of concept development through hot reload and mature tooling.
- Component based structure encourages reuse across roles, such as shared complaint lists and detail views.
- Strong TypeScript integration improves reliability through typed state, props, and API payloads.
- Well established accessibility patterns support inclusive design from the start.

Negative:
- Higher client side complexity compared to server rendered pages, especially around state and routing.
- Performance tuning and bundle size management require attention as features grow.

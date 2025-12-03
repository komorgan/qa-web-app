# Traceability Matrix – Leantime Testing

| Requirement ID | Description                                      | Test ID(s)        | Evidence Location                       |
|----------------|--------------------------------------------------|-------------------|-----------------------------------------|
| FR-1           | User authentication (login/logout)               | F1                | tests/functional, screenshots, logs     |
| FR-2           | Role-based authorization (RBAC)                  | F2                | tests/functional, screenshots, logs     |
| FR-3           | CRUD lifecycle on tasks                          | F3                | tests/functional, DB snapshots          |
| FR-4           | Validation and error handling                    | F4                | tests/functional, API/UI error outputs  |
| FR-5           | Search/filter and pagination on tasks            | F5                | tests/functional, screenshots           |
| NFR-P1         | Baseline performance                             | P1                | tests/performance, perf charts          |
| NFR-P2         | Stress / breakpoint performance                  | P2                | tests/performance, perf charts          |
| NFR-S1         | Dynamic security scan (DAST)                     | S1                | tests/security, scan report             |
| NFR-S3         | Injection resilience                             | S3                | tests/security, logs/screenshots        |
| NFR-U1         | Usability/accessibility of key flows             | U1                | tests/nfr, accessibility reports        |
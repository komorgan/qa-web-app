# Test Plan – Leantime (Track B)

## 1. Objectives and Scope
- System Under Test (SUT): Leantime (open-source project management web app).
- Track: B – Deploy & Test existing OSS.
- Scope: Authentication, RBAC, CRUD on tasks, search/filter/pagination,
  performance under load, and security posture of key flows.

## 2. Assumptions and Risks
- Leantime is deployed locally via Docker with a real database.
- Team members can access the SUT on their own machines.
- Key risks:
  - Environment drift between team members.
  - Incomplete coverage of edge cases in auth and RBAC.
  - Performance tests affecting the stability of local machines.

## 3. Test Environment
- Application: Leantime (Docker containers for app + DB).
- Base URL (example): http://localhost:8080
- Dedicated test database/schema.
- Seed data: test users, roles, projects, and tasks.

## 4. Test Types and Selection
- Functional tests (F1–F5):
  - Authentication, authorization (RBAC), CRUD tasks, validation, search/filter/pagination.
- Non-functional tests (NFRs):
  - Performance (P1 baseline, P2 stress),
  - Security (S1 DAST, S3 injection),
  - Usability/accessibility (U1).

## 5. Quality Gates
- Build/deploy smoke test passes; SUT is reachable.
- All required functional tests pass with no critical path failures.
- Performance: p95 latency and error rates meet agreed thresholds.
- Security: No unresolved High severity issues from dynamic scanning.

## 6. Traceability
- Requirements: FR-x (functional), NFR-x (non-functional).
- Tests: F1–F5, P1–P2, S1–S3, U1, etc.
- Evidence: Logs, screenshots, DB snapshots, reports.

See `traceability-matrix.md` for the detailed mapping.
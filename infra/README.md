# Infra / SUT Setup Notes

This folder documents how to run the System Under Test (SUT) locally.
The SUT is the Leantime open-source project management web application,
deployed via Docker with a real MySQL/MariaDB database.

High-level expectations:
- Leantime is running locally (e.g., http://localhost:8080).
- A dedicated database/schema is used for tests.
- Test users, roles, projects, and tasks are created as described in the test plan.

For detailed step-by-step local setup instructions, see `../docs/local-setup.md`.
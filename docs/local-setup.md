Local Setup Guide (Leantime Track B Testing)

This guide explains how each team member can set up the System Under Test (Leantime) and run the tests from this repository.

The goals are:

-Everyone can run Leantime locally (Docker + MySQL).

-Everyone can run the shared test suites against their own Leantime instance.

1. Prerequisites

Install the following on your machine:

-Git

-Docker Desktop (includes Docker and Docker Compose)

-A code editor (for example, VS Code)

-A modern web browser (for example, Chrome, Firefox, Edge)

On Windows, make sure Docker Desktop is running before you start the containers.

2. Clone this testing repository

Open Command Prompt or PowerShell and run:

git clone https://github.com/komorgan/qa-web-app.git leantime-testing
cd leantime-testing


You should now see folders like:

infra

tests

docs

.github

3. Create a folder for the System Under Test (Leantime)

The Leantime application itself (SUT) lives in a separate folder from this repo.

From inside leantime-testing, go one level up and create a folder for the SUT:

cd ..
mkdir leantime-sut
cd leantime-sut


Your directory structure should look like this:

<parent-folder>/
  leantime-testing/   # this Git repo (tests, docs, CI)
  leantime-sut/       # Leantime app + database (Docker)

4. Download Leantime’s Docker configuration

In the leantime-sut folder you need:

docker-compose.yml

.env (copied or adapted from the example in the official Leantime Docker repo)

Follow the Leantime Docker instructions to obtain these files and place them in leantime-sut.

When you are done, leantime-sut should look like:

leantime-sut/
  docker-compose.yml
  .env

5. Configure .env for your local environment

Open the .env file in a text editor.

Set at least:

The database host (usually the DB service name from docker-compose.yml, for example db).

The database user, password, and database name.

The Leantime base URL, for example:

LEANTIME_BASEURL=http://localhost:8080

Make sure the port matches the one used in docker-compose.yml.

6. Start Leantime (Docker containers)

In Command Prompt or PowerShell, while in leantime-sut, run:

docker compose up -d


This should start:

A database container (MySQL or MariaDB)

A Leantime application container (web app)

Check that they are running:

docker ps


You should see at least two containers, one for the DB and one for Leantime.

7. Initial Leantime setup in the browser

Open your browser and go to the base URL from .env, for example:

http://localhost:8080


On first run you will see a setup or installation page:

Confirm the database connection.

Create the first admin user (email, password, company name).

Log in as the admin user.

Create shared test data (details should match the test plan):

One or more admin users.

At least one lower-privilege user (for example, Editor).

At least one restricted user (for example, Read-only).

One or more projects.

A reasonable number of tasks in those projects for CRUD and search/pagination tests.

8. Running tests from this repository

After the SUT is running, go back to the testing repo:

cd ../leantime-testing


From here:

Functional tests live in tests/functional/.

Performance tests live in tests/performance/.

Security tests live in tests/security/.

Other non-functional tests (usability, reliability, compatibility) live in tests/nfr/.

Each folder contains a README.md with specific instructions on how to run those tests.

9. Troubleshooting

If the browser cannot reach Leantime:

Check containers with:

docker ps


Confirm the port in the URL matches docker-compose.yml.

Inspect logs:

docker logs <leantime-container-name>
docker logs <db-container-name>


If tests fail to connect to Leantime:

Confirm the base URL in the test configuration matches the Leantime URL.

Make sure Leantime is running and you can log in manually.
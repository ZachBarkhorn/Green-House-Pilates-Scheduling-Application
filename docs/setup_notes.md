# Pilates Scheduling App: Capstone Game Plan

> **Reference:** Planning notes from the Claude chat **"Pilates Scheduling Capstone Project"** (September 29, 2026).

---

## Infrastructure Note: Linux VM (Optional, Decide Later)

A cloud Linux VM is **not required**. Azure Container Apps can host the app without one.

| Option | Cost | What it adds |
|---|---|---|
| **Skip the VM** | $0 | Simplest path. Loses the server-hardening story. |
| **Local VM** (Hyper-V or Multipass) | $0 | Practice target for Ansible and CIS/STIG hardening, without cloud cost. |
| **Azure Linux VM** | Free for 12 months, then paid | A real internet-facing server: SSH hardening, firewall rules, patching, reading live attack logs. |

**Decision:** Deferred. Not needed until well after the app works.

---

## Roadmap: Next Sessions

Work in order, because each phase produces the next phase's inputs. **Design comes before code**, per the SSDLC.

### 1. Finish Acceptance Criteria and Add Security Criteria

- [ ] Write every criterion in **Given / When / Then** format so it can later become an automated test
- [ ] Add at least one **security criterion** per story
  - *Example:* Given a client, when they call the ban endpoint, then the server returns `403 Forbidden`
  - Cover input validation and rate limiting
- [ ] Write **misuse cases**, for example:
  - A client books a class for someone else
  - A user replays a Stripe webhook

**Deliverable:** A complete set of user stories with functional and security acceptance criteria.

### 2. Scope the MVP and Set Up the Backlog

- [ ] Prioritize the stories with **MoSCoW** (Must / Should / Could / Won't), and define the smallest version the studio could actually use
- [ ] **Classify the data:** what counts as personal information, and what payment data Stripe handles (the app never touches card numbers)
- [ ] Load the must-have stories into **GitHub Issues** and track them on a **GitHub Projects** board (Agile workflow)

**Deliverable:** The MVP backlog and a data classification table.

### 3. Design

- [ ] **Architecture diagram** of the Azure layout (Static Web Apps, Container Apps, Container Registry, PostgreSQL, Key Vault)
- [ ] **Database schema (ERD):** users, roles, classes, sessions, bookings, payments
- [ ] **API endpoint outline**
- [ ] **Architecture Decision Records (ADRs)** for the major choices:
  - PostgreSQL over MongoDB
  - Azure Container Apps over a full Kubernetes cluster

**Deliverable:** Architecture diagram, ERD, API outline and ADRs.

### 4. Threat Model

- [ ] Draw a **data flow diagram** and analyze it with **STRIDE**
- [ ] Turn each threat into a new acceptance criterion or test (feeds back into Phase 1)
- [ ] Update the **requirements traceability matrix**, which links each requirement to its design, test and mitigation (CSSLP alignment)

**Deliverable:** Threat model and updated requirements.

### 5. Development Environment

- [ ] Set up **WSL2 (Ubuntu)** as the development environment
- [ ] Create the GitHub repo with **branch protection** rules
- [ ] Add a **pre-commit hook** that runs **Gitleaks** to catch secrets
- [ ] Get a basic "hello world" API talking to PostgreSQL in **Docker Compose**

**Deliverable:** `docker compose up` runs the skeleton app.

### 6. CI Pipeline and First Feature

- [ ] Set up **GitHub Actions** to run lint, tests, **Semgrep** (SAST) and **Trivy** (container scanning) on every pull request
- [ ] Build the **admin ban/unban flow** with server-side authorization. Its acceptance criteria from Phase 1 become the tests.

**Deliverable:** First feature merged through a pipeline that enforces security checks.

---

## Milestone: Resume-Ready

After Phase 6, the project is ready to add to the resume.

**Later phases:** Terraform (Infrastructure as Code), Azure deployment, and Kubernetes (a temporary `kind` cluster in CI running integration tests and an OWASP ZAP scan).

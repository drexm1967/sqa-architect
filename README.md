# SQA Architect Repository

![CI Status](https://github.com/drexm1967/automation-lab-ecosystem/workflows/CI%20-%20API%20Test%20Suites/badge.svg)
![Python Tests](https://img.shields.io/badge/Python%20Tests-130%20passing-success)
![Java Tests](https://img.shields.io/badge/Java%20Tests-130%20passing-success)
![Playwright Tests](https://img.shields.io/badge/Playwright%20Tests-130%20passing-success)
![Performance Tests](https://img.shields.io/badge/Performance%20Tests-k6%20%7C%20JMeter-success)
![Security](https://img.shields.io/badge/Security-OWASP%20ZAP-success)
![Test Frameworks](https://img.shields.io/badge/Frameworks-pytest%20%7C%20TestNG%20%7C%20Playwright-blue)
![License](https://img.shields.io/badge/license-MIT-blue)

📊 **[View Live Test Report](https://drexm1967.github.io/sqa-architect/)** (Always available after CI/CD deployment)
   
   **[More about the AUT](https://github.com/drexm1967/sqa-architect/wiki#about-the-application-under-test-aut)**

 ## Overview

This repository has been created for publishing the live Allure report for my continuously evolving QA automation ecosystem, within the private **automation-lab-ecosystem** repository, demonstrating professional testing practices across the full SDLC. It is part of a portfolio project that showcases expertise in API/UI test automation, CI/CD integration, infrastructure-as-code and use of AI as a collaborative tool.

## Why This Project

Rather than isolated test scripts, this ecosystem demonstrates:

- **Real-world complexity**      : Full application with authentication, CRUD operations, business logic
- **Multiple testing paradigms** : Python pytest + Java TestNG + Playwright TypeScript in the same pipeline
- **Performance validation**     : k6 and JMeter suites with threshold enforcement on every CI push
- **Security validation**        : OWASP ZAP API scan driven by OpenAPI spec on every CI push
- **Infrastructure as code**     : Docker Compose with profile-based architecture for resource optimization
- **CI/CD integration**          : Automated testing on every commit with comprehensive reporting
- **Professional practices**     : Proper branching strategy, meaningful commits, production-ready patterns
- **Portfolio showcase**         : Public GitHub Actions reports, Allure dashboards, status badges

**This isn't a tutorial follow-along - it's a demonstration of professional QA automation engineering.**

## What's Implemented

### ✅ API Test Automation (Complete)
- **Python Test Suite**: 130 tests using pytest + requests
  - Authentication & authorization flows
  - CRUD operations for users, products, orders
  - Pagination, filtering, search functionality
  - Negative test cases and error handling
  - Allure reporting integration

- **Java REST Assured Suite**: 130 tests using TestNG + REST Assured
  - BDD-style test organization
  - Comprehensive API endpoint coverage
  - TestNG retry mechanism for flaky tests
  - Allure reporting integration

- **Playwright TypeScript Suite**: 130 tests using Playwright test runner
  - Cross-framework validation of the same API endpoints
  - TypeScript for type safety and IDE support
  - Mirrors Python and Java coverage for cross-suite verification
  - Allure reporting integration

### ✅ Performance Test Automation (Complete)
- **k6 Suite**: 6 scenarios covering all endpoint groups
  - health, auth, users, products, orders, user journey
  - 10 VUs, 30s sustained load, 5s ramp-up/ramp-down
  - Strict performance thresholds enforced per scenario
  - Custom Allure integration via convert-to-allure.js
  - Executes on every CI push

- **JMeter Suite**: 6 test plans mirroring k6 coverage
  - health, auth, users, products, orders, user journey
  - 10 VUs, 30s sustained load (mirrors k6 parameters)
  - setUp thread group pattern for shared admin token across VUs
  - RFC-4180 compliant JTL parser for Allure conversion
  - Custom Allure integration via convert-jtl-to-allure.js
  - Executes on every CI push

### ✅ Security Test Automation (Complete)
- **OWASP ZAP API Scan**: spec-driven active + passive scan
  - Driven by OpenAPI 3.0.3 spec (docs/openapi.yaml) — full attack surface coverage
  - ZAP Automation Framework (YAML-based) — ZAP's documented forward direction
  - Passive scan + active scan on every CI push
  - CI threshold: fail on High risk alerts; Medium findings tracked and documented
  - HTML report artifact + JSON report for Allure conversion
  - Custom Allure integration via convert-zap-to-allure.js
  - Risk mapping: High=failed, Medium=broken, Low/Informational=passed

### ✅ Application Under Test
- **Express.js REST API** with JWT authentication
- **PostgreSQL 15** database with realistic schema
- **Seeded test data**: 120 users, 150 products, 200 orders
- RESTful endpoints for auth, users, products, orders
- Health check and monitoring endpoints
- **OpenAPI 3.0.3 spec**: docs/openapi.yaml — 19 endpoints, full schemas, validated with Spectral
- **React UI client**: served by Express at `/products`; root `/` remains an API JSON response

### ✅ Infrastructure
- **Docker Compose** with profile-based architecture
  - `core`: PostgreSQL, Redis, Express app
  - `selenium`: Selenium Grid (hub + Chrome + Firefox nodes)
  - `cicd`: Jenkins
  - `monitoring`: Grafana + Prometheus
  - `extras`: WireMock, MailHog, Portainer
- **Memory-optimized** for 8-10GB VM environments

### ✅ CI/CD Pipeline
- **GitHub Actions** workflow
  - Automated test execution on push/PR
  - Parallel Python, Java, Playwright, k6, JMeter, and ZAP runs
  - Unified Allure report generation across all six suites
  - GitHub Pages deployment on every push to main
  - PR notifications with test results

### 🚧 In Development
- UI automation (Selenium Java POM + Playwright TypeScript) **In Progress**
- Contract testing (Pact)
- Locust performance scenarios

## Technology Stack

| Category             | Technologies                                                            |
|----------------------|-------------------------------------------------------------------------|
| **Languages**        | Java 17, Python 3.12, TypeScript, JavaScript (Node.js 20)              |
| **API Testing**      | REST Assured, pytest + requests, Playwright (TypeScript)                |
| **Performance**      | k6, JMeter 5.6.3                                                        |
| **Security**         | OWASP ZAP 2.17.0                                                        |
| **Test Frameworks**  | TestNG, pytest, Playwright Test Runner                                  |
| **Build Tools**      | Maven, pip, npm                                                         |
| **Databases**        | PostgreSQL 15, Redis 7                                                  |
| **Infrastructure**   | Docker, Docker Compose                                                  |
| **CI/CD**            | GitHub Actions                                                          |
| **Reporting**        | Allure Reports (unified — Python, Java, Playwright, k6, JMeter, ZAP)   |

**Pipeline includes:**
1. PostgreSQL + Express app setup (per job)
2. Python API test suite execution (130 tests)
3. Java API test suite execution (130 tests)
4. Playwright API test suite execution (130 tests)
5. k6 performance suite execution (6 scenarios)
6. JMeter performance suite execution (6 test plans)
7. OWASP ZAP API security scan
8. Playwright UI test suite execution (82 tests)
9. Unified Allure report generation across all six suites
10. GitHub Pages deployment
11. PR comment with test results

## Application Under Test

**Express.js REST API** running on port 3000:

### Endpoints

| Endpoint             | Method              | Description                          | Auth Required |
|----------------------|---------------------|--------------------------------------|---------------|
| `/`                  | GET                 | API info and endpoint listing (JSON) | No            |
| `/health`            | GET                 | Health check                         | No            |
| `/api/auth/register` | POST                | User registration                    | No            |
| `/api/auth/login`    | POST                | User login                           | No            |
| `/api/auth/me`       | GET                 | Current user                         | Yes           |
| `/api/users`         | GET                 | List users                           | Yes           |
| `/api/users/:id`     | GET/PUT/DELETE      | User operations                      | Yes           |
| `/api/products`      | GET                 | List products                        | No            |
| `/api/products/:id`  | GET/POST/PUT/DELETE | Product operations                   | Yes/Admin     |
| `/api/orders`        | GET/POST            | Order operations                     | Yes           |
| `/api/orders/:id`    | GET/PATCH/DELETE    | Order management                     | Yes/Admin     |

### Authentication

- **JWT tokens** with 24-hour expiration
- **Test credentials**:
  - Admin: `admin1@testlab.com` / `Test@1234`
  - Regular user: Created dynamically in tests
- **Roles**: `user` (default), `admin`

### Database

**PostgreSQL 15** with seeded test data:
- 120 users (including 3 admins)
- 150 products across 10 categories
- 200 orders with order items
- Realistic relationships and data

## Docker Infrastructure

Profile-based architecture for selective service startup:

```bash
# Core services only (~1.4GB RAM)
docker compose --profile core up -d

# Add Selenium Grid for UI tests (~3.9GB RAM total)
docker compose --profile core --profile selenium up -d

# Add Jenkins for CI/CD demos (~4.9GB RAM total)
docker compose --profile core --profile selenium --profile cicd up -d

# Everything (~6.7GB RAM total)
docker compose --profile core --profile selenium --profile cicd --profile monitoring --profile extras up -d
```

**Memory limits configured** for optimal performance on 8-10GB VMs.

## Reporting

### Unified Allure Reports

All test suites contribute to a single Allure report with:
- Test execution history and trends across all frameworks
- Categorization by suite, feature, and story
- Attachments (logs, request/response data)
- Test duration analytics
- Flaky test detection
- Security scan results alongside functional and performance results

**View unified report in CI/CD:**
- Deployed automatically to GitHub Pages on every push to main
- URL: `https://drexm1967.github.io/sqa-architect/`

## Known Issues

### TestNG Retry Mechanism
4 tests show cosmetic retry failures (Run 1 fails, Run 2 passes):
- `AuthTest.testSuccessfulLogin`
- `AuthTest.testSuccessfulRegistration`
- `HealthTest.testHealthEndpoint`
- `HealthTest.testRootEndpoint`

**Root cause**: REST Assured spec initialization timing  
**Impact**: Cosmetic only — all tests pass on automatic retry but causes CI to show as failed.  
**Status**: Documented, not blocking

### ZAP Security Findings (Medium — Deferred)
3 Medium risk findings identified by ZAP API scan:
- CSP: Wildcard Directive
- CSP: style-src unsafe-inline
- Cross-Domain Misconfiguration (Access-Control-Allow-Origin: *)

**Impact**: CI does not fail on Medium findings (threshold: High only)  
**Status**: Retained as case study material demonstrating real-world security finding triage

### UI Defect Findings (Retained as evidence of UI test effectiveness)
5 defects surfaced by UI automation tests
| Root Cause                                                           | Type  | # of Affected Tests |
|----------------------------------------------------------------------|-------|---------------------|
| `client.js` 401 redirect on `requiresAuth=false`                     | App   |       2             |
| Missing `noValidate` on Login/Register forms                         | App   |       2             |
| `<label>` not associated with `<select>` via `htmlFor/id`            | App   |       6             |
| No auth-guard redirect on `/login for` authenticated users           | App   |       1             |
| `data.total` → should be `data.pagination.total` (Products + Orders) | App   |       3             |

## Contributing

This is a portfolio and learning project. While not actively seeking contributions, feedback and suggestions are welcome via GitHub issues.

## Project Evolution

This is a **living project** with continuous updates and improvements:

- ✅ **Phase 1**: Core API + Performance Testing (**Complete**)
  - Express.js REST API with JWT authentication
  - PostgreSQL database with realistic test data
  - Python API test suite (130 tests)
  - Java REST Assured suite (130 tests)
  - Playwright TypeScript API suite (130 tests)
  - k6 performance suite (6 scenarios)
  - JMeter performance suite (6 test plans)
  - Docker infrastructure with memory optimization
  - GitHub Actions CI/CD pipeline with unified Allure reporting
  - React UI client served by Express at `/products`
  - OpenAPI 3.0.3 spec (docs/openapi.yaml)
  - OWASP ZAP API security scan

- 🚧 **Phase 2**: UI Testing (In Progress)
  - UI automation with Playwright (TypeScript) (**Completed**)
  - UI automation with Selenium (Java, Page Object Model) (**In progress**)
  - Visual regression testing
  - Cross-browser testing matrix

- 📋 **Phase 3**: Extended Testing Patterns (Planned)
  - Locust stress testing scenarios
  - Contract testing with Pact (consumer-driven)
  - BDD with Cucumber/Behave
  - Jenkins pipeline as code
  - Newman/Postman collections

## ISTQB Alignment

This project has been constructed to also demonstrate competencies aligned with:
- **ISTQB Foundation Level** (CTFL v4.0)
- **ISTQB Test Automation Engineering** (CTAL-TAE v2.0)
- **AT\*SQA Test Automation MicroCredentials**

Specific coverage includes: test automation architecture, framework design, performance test design, security test design, CI/CD integration, test environment management, and defect management processes.

## License

MIT License - See [LICENSE](LICENSE) file for details.

## About

**Author**  : Drexel McMillan  
**Purpose** : Portfolio project demonstrating professional QA automation engineering expertise  
**Target**  : Corporate employment and 1099 contracting opportunities in Software Quality Assurance and Test Automation

### Connect
Hiring managers and technical recruiters are welcome to contact me to schedule a technical walkthrough and in-depth discussion of the private repository and its contents as part of role evaluations.

- **Email** : sqalab.admin@protonmail.ch

---

- **Repository Status:** Active Ongoing Development  
- **Last Updated:** 14 March 2026
- **Test Success Rate:** 74.27% (I broke some stuff and it's awesome!!!)
- **Coverage Goal:**  90% or better
  
> *"Quality is not an act, it is a habit."* - Aristotle

Built with precision, tested with purpose, deployed with confidence.

---

## Copyright Notice

**© 2026 Drexel McMillan.** This project was designed and implemented
by Drexel McMillan as a professional portfolio demonstration.

Git commit history and timestamps serve as proof of authorship.
Any misrepresentation of this work as original to another party
constitutes intellectual property theft and intent to commit fraud.

---

## Diligence Statement

In the creation of the content contained within this project, I used Claude Sonnet 4.6 Pro to assist in text creation and refinement, coding, architectural design, and implementation. I affirm that all AI-generated and co-created content underwent thorough vetting, editing, and curation by the human co-author. The final product accurately reflects my understanding, expertise, and intended meaning. While an AI tool was instrumental in the development, implementation, and testing process, I maintain full responsibility for the content, its accuracy, and its presentation. This disclosure is made in the spirit of transparency and to acknowledge the evolving role of AI in content creation and other intellectual work.

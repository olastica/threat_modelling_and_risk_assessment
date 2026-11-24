# Student Login Portal | Threat Modeling & Risk Assessment

**Halisans Technologies  
**Analyst:** [Olasunkanmi Ogidan] · 
**Status:** Production security audit

## Executive summary

This repository documents a security assessment of a proposed **Student Login Portal**. Students can **register**, **log in**, and **view their own academic profiles**. The assessment uses an OWASP Threat Dragon data flow diagram (DFD), STRIDE threat identification, a risk register, security control mapping, and a risk treatment plan.

## Application scope

- **External entity:** Student using a web browser
- **Three application processes:** Student Registration, Student Login, View Student Profile
- **Data store:** Student Database containing student accounts, password hashes, and academic profile records
- **Known communication:** Student/browser ↔ application via HTTPS/TLS
- **To confirm with developers:** backend-to-database protocol, database hosting, session mechanism, and authorization enforcement
- **Out of scope:** administrator functions, profile data import, penetration testing, and live production systems

## Objectives

1. Translate the developer brief into a Level 1 DFD with **exactly three application processes**.
2. Label data flows and known protocols, and document.
3. Identify and justify the trust boundaries.
4. Apply STRIDE to identify plausible threats.
5. Score likelihood and impact (1–5), then document controls and treatment actions.

## Assessment workflow

`Developer brief → Threat Dragon DFD → STRIDE findings → Risk register → Control mapping → Risk treatment plan`

| Stage | What I did | Evidence |
|---|---|---|
| Model | Created DFD and labeled data flows / boundaries | [`screenshot`](threat-model/screeshot.png), [`model`](threat-model/student_web_portal.json), [`report`](threat-model/student_web_portal.pdf) |
| Threats | Identified threats using STRIDE | Threat Dragon report in `threat-model/` |
| Risk | Scored each threat and recorded justification | [`risk-assessment/`](risk-assessment/) |
| Controls | Mapped mitigations to applicable controls | [`control-mapping/`](control-mapping/) |
| Treatment | Assigned proposed actions, owners, and verification criteria | [`risk-treatment/`](risk-treatment/) |

## Findings summary

| ID | STRIDE category | Threat summary | Risk score | Proposed action |
|---|---|---|---|---|
| R-001 | [Spoofing] | [A threat actor uses stolen or phished credentials, or a hijacked session token, to impersonate a legitimate student.] | [20] | [Mitigate] |
| R-004 | [Tampering] | [A threat actor injects malicious SQL through portal input fields to alter or delete student records in the database.] | [25] | [Mitigate] |
| R-005 | [Repudiation] | [A threat actor forges or injects log entries to hide their actions, so activity cannot be traced to an account.] | [10] | [Mitigate] |
| R-006 | [Information Disclosure] | [A threat actor intercepts traffic or exploits access flaws to read other students' personal data or password hashes.] | [15] | [Mitigate] |
| R-007 | [Denial of Service] | [A threat actor floods the portal with requests, exhausting server or database resources and blocking legitimate students.] | [15] | [Mitigate] |
| R-008 | [Elevation of Priviledge] | [An authenticated student or attacker exploits access-control or server flaws to gain administrator or root privileges.] | [15] | [Mitigate] |

**Risk scoring:** Likelihood (1–5) × Impact (1–5). Explain both ratings in the risk register. Scores are scenario judgments, not measured exploit probabilities.

## Deliverables

1. **OWASP Threat Dragon report and model** — add exported report PDF and model JSON to `threat-model/`.
2. **Threat Risk Register** — complete `risk-assessment/threat-risk-register.csv`.
3. **Control Mapping** — complete `control-mapping/control-mapping.csv` using verified control references.
4. **Risk Treatment Plan** — complete `risk-treatment/risk-treatment-plan.csv`.

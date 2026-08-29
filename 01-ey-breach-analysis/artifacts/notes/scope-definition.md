# Project Scope Definition – Ernst & Young Breach Analysis
This document defines the analytical boundaries, objectives, and methodology for the EY Breach Analysis project. It provides internal guidance for how each artifact, analysis track, and report contributes to the overall assessment of EY’s externally visible attack surface.

## 1. Purpose of the Project

To evaluate how Ernst & Young's publicly accessible operational disclosures, including job postings and vendor case studies, expand the organization's attack surface and provide threat actors with actionable reconnaissance pathways. The project integrates OSINT analysis, threat modeling, supply-chain risk evaluation, and governance assessment.

## 2. Scope Components
### 2.1 OSINT Exposure
Analyze externally visible artifacts that reveal:
-   defensive tooling (SIEM, EDR, logging architecture) 
-   SOC workflows and escalation thresholds 
-   platform integrations (ServiceNow, identity providers, ticketing systems)
-   supply‑chain dependencies
-   operational maturity indicators

Artifacts in this category include:
-   `ey-job-posting-analysis.md`
-   `servicenow-case-study-analysis.md`
-   `public-disclosure-risk-notes.md`
### 2.2 Threat Reconnaissance Pathways
Model how adversaries can use OSINT disclosures to:
-   identify detection gaps
-   infer architectural weaknesses
-   map supply‑chain attack paths
-   design intrusion strategies that avoid escalation
-   exploit predictable SOC workflows

Artifacts in this category include:
-   `attacker-reconnaissance-path.md`
-   `supply-chain-attack-surface.md`
-   `cve-correlation-servicenow.md`
### 2.3 Governance & Third-Party Risk Implications
Evaluate EY’s governance posture by assessing:
-   external‑facing communication controls
-   oversight gaps in public disclosures
-   risks introduced by deeply integrated platforms
-   third‑party exposure through ServiceNow and related vendors
-   alignment with GRC best practices

Artifacts in this category include:
-   `governance-failures.md`
-   `third-party-risk-implications.md`
-   `osint-exposure-risk-category.md`
## 3. Out-of-Scope Items
The following areas are intentionally excluded:
-   internal EY systems not publicly documented
-   non‑public breach data
-   forensic analysis
-   incident response activities
-   red‑team simulation beyond OSINT‑derived pathways

This ensures the project remains strictly OSINT‑driven and publicly sourced.
## 4. Methodology
The project uses a multi‑stage TI + GRC methodology:

1.  **OSINT Collection**   
Gather publicly available artifacts relevant to EY’s defensive posture.
2.  **Exposure Analysis**   
Identify operational details disclosed through job postings and case studies.
3.  **Threat Modeling**   
Map attacker pathways using MITRE ATT&CK, supply‑chain vectors, and SOC workflow exploitation.
4.  **Governance Evaluation**   
Assess communication controls, oversight gaps, and third‑party risk implications.
5.  **Synthesis & Reporting**   
Produce a breach‑analysis report, findings summary, and remediation recommendations.
## 5. Deliverables
-   OSINT source analyses
-   threat reconnaissance models
-   supply‑chain attack surface evaluation
-   governance and risk assessments
-   diagrams illustrating attack paths
-   final breach‑analysis report
-   findings summary
-   remediation recommendations
## 6. Status
This is an active project; analysis is in progress.  
Artifacts will be added and updated as each section is completed.

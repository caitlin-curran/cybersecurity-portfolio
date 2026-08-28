# How Job Postings Become OSINT for Threat Actors
Prepared by: Caitlin Curran  
28 August 2026
## Introduction
Job postings provide an oft-overlooked source of organizational intelligence. Because hiring teams want to attract candidates who have already used the tools required for the position, they often unintentionally disclose platforms that are in use. Due to this tendency, attackers often analyze job postings as part of their reconnaissance activities.

Because job postings are public, indexed, and written by the organization itself, they serve as a valuable source of intelligence for threat actors. Hiring teams write job descriptions to maximize keyword matching and are likely unaware of the security implications of listing specific platforms. Due to the nature of certain roles, some job descriptions can reveal an organization's entire defensive stack. In addition to the specific platforms being used, job descriptions can also signal program maturity and team structure. These are operational details that the organization would otherwise not disclose publicly.

## Analysis of Ernst & Young Job Posting[^1]
[^1]: *Source: Ernst & Young — SOC L1 Analyst job posting (EY Careers, accessed August 11, 2026).*

In a public job posting for a SOC L1 Analyst, Ernst & Young (EY) reveals both the tools being used and their operational structure. The posting explicitly lists Splunk, Sentinel, CrowdStrike, Microsoft Defender, and ServiceNow as required skills for the role. This list alone reveals the environment, SOC maturity, and weak points. The Key Responsibilities listed in the posting point to a tiered, tool-driven SOC model in which employees are expected to meet service-level targets.

This job posting provides an adversary with actionable intelligence. Tooling disclosures and workflow descriptions in the job posting reveal operational structure. The explicit listing of Splunk, Sentinel, CrowdStrike, Microsoft Defender, and ServiceNow provides a clear picture of EY's defensive posture and potential weak points, while the Key Responsibilities section points to a tiered SOC model, indicating escalation thresholds, triage workflows, and standardized documentation practices.

### Information Gained from Tooling Disclosures

An attacker can gain a wealth of actionable intelligence from tooling disclosures.
 - The listing of both Splunk and Sentinel indicates that EY runs a dual-SIEM environment.
	 - Dual-SIEM environments are complex and often misconfigured. This tells an attacker there are likely gaps to exploit.
 - The presence of both CrowdStrike and Microsoft Defender suggests a multi-EDR environment.
	- This indicates to an attacker that an alternate path of entry may be available if the first one fails. 
	- Microsoft Defender indicates that Azure AD/Entra ID is being used.
 - The inclusion of ServiceNow reveals that EY relies on a deeply integrated workflow and ticketing platform that touches ITSM, ITOM, HRSD, automation, and AI agents in addition to storing tickets, attachments, logs, chat transcripts, HR data, and workflow history.
	- Because ServiceNow connects to identity systems, EDR, SIEM, HR platforms, and remote support tools, this presents an attacker with a broad, highly interconnected attack surface.
	- ServiceNow has a history of authentication bypasses, API flaws, plugin issues, MID server vulnerabilities, and misconfigurations.
		- This presents a significant supply-chain exposure that attackers can leverage during reconnaissance.
	- ServiceNow has the potential to provide an attacker with access to the entire operational environment.

This combination of tools provides an attacker with several potential weak points that could be exploited to gain entry.

 - ServiceNow integrations
 - SIEM ingestion pipelines
 - EDR exceptions
 - Identity misconfigurations
 - Automation pipelines
 - Ticketing attachments
 - API endpoints
 - Third-party support access
 - Known CVEs

### Information Gained from Key Responsibilities
The job posting explicitly mentions Senior Security Analysts, SOC Engineering, and Incident Response teams. This tells an attacker that EY uses a multi-tier SOC structure with three response levels and engineers to handle tooling and detection logic. This structure indicates:
 - Predictable escalation paths
 - Predictable handoff delays
 - Predictable documentation patterns
 - Predictable gaps between tiers

These are all pathways that an attacker could exploit.

The first listed responsibility requires monitoring of SIEM, EDR, and NDR. This tells an attacker that EY's SOC is tool-driven and that alerts are triaged by L1 Analysts, not simply automated pipelines. Tool-driven SOCs have predictable weaknesses that adversaries will consider when choosing evasion strategies.

Another responsibility shows that L1 Analysts are responsible for documenting security alert analysis and investigation steps. From this information, combined with the disclosed tooling, an attacker can infer that EY uses ServiceNow for ticketing and that tickets will contain investigation notes, attachments, and logs. This would lead an adversary to conclude that compromising ServiceNow would allow them to see gaps in coverage, detection patterns, and escalation logic.

The responsibility to "deliver services according to service targets (SLAs)" indicates that EY's SOC is service-level-driven, presenting an attacker with several predictable weaknesses to exploit. SLA-driven SOCs often:

 - Rush triage
 - Close alerts prematurely
 - Rely on automation
 - Miss subtle anomalies
 - Struggle with multi-stage attacks
 
 The expectation that L1 Analysts will escalate complex investigations tells an attacker that L1 Analysts only handle low-complexity alerts and that there is a defined escalation threshold. This suggests the adversary may be able to avoid detection by staying under the escalation threshold.

## Job Postings as a Reconnaissance Starting Point

Job postings are passive, low-risk sources of information that are authoritative because they are written by the organization itself. Job descriptions often unintentionally reveal technologies, workflows, and operational structures before an attacker even touches a system. Adversaries can combine disclosures from job postings with vendor case studies, public documentation, CVE databases, breach reports, and employee LinkedIn profiles to map a picture of the environment before attempting active reconnaissance.

Attackers use listed platforms to identify relevant vulnerabilities, research misconfiguration patterns, and anticipate detection capabilities and gaps. Similarly, they use role descriptions as behavioral intelligence to infer escalation thresholds, triage workflows, and alert-handling expectations. This helps predict how defenders will respond to different intrusion strategies.

Adversaries prefer to start with passive reconnaissance because gathering information without touching the network allows them to avoid detection and identify weak points before committing to an intrusion path. This reconnaissance also helps them to tailor attacks to stay below detection thresholds or escalation triggers, thereby increasing the likelihood of a successful breach.

Job postings act as an initial reconnaissance layer used to inform deeper OSINT research. They help attackers design targeted intrusion strategies that avoid detection and should therefore be treated as part of the organization's external attack surface.

## Implications & Considerations
Because revealed platforms may align with known CVEs or exploit kits, publicly disclosed tooling increases exposure to targeted exploitation by unintentionally guiding adversaries toward third-party weaknesses. Additionally, operational details revealed in job descriptions may lead attackers to exploitation paths that help them avoid detection.

To mitigate these risks, job postings should be treated as externally visible artifacts requiring security review before publication. Policies should provide sanitization guidelines to remove vendor names, architectural details, and internal organizational structures.

## Conclusion
Job postings are reconnaissance vectors that can supply adversaries with valuable information about an organization's security posture. To accurately assess risk and exposure, hiring communications must be included in an organization's attack surface. Sanitizing job postings reduces OSINT exposure while strengthening both TI and GRC posture.

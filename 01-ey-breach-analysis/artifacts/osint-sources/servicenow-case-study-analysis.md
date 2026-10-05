# Public Technology Disclosures and Attacker Reconnaissance: Analysis of the EY ServiceNow Case Study
Prepared by: Caitlin Curran  
5 October 2026
## Introduction

Designed to showcase business success and technology adoption, vendor case studies can inadvertently provide threat actors with a detailed understanding of how an organization operates. By highlighting a vendor's products and demonstrating how they are used in real-world environments, case studies frequently reveal technologies, business processes, integrations, and operational dependencies that can inform attacker reconnaissance.

Vendor case studies are public, indexed, and often authored or approved by the organization itself. When an organization participates in a vendor case study, it is publicly disclosing information about the products, services, and capabilities used within its environment. While any individual disclosure may appear innocuous, the intelligence value of vendor case studies lies not in any single detail, but in their ability to reduce uncertainty and enable attackers to construct increasingly accurate models of a target environment.

This analysis examines a publicly available ServiceNow case study featuring Ernst & Young (EY) to demonstrate how seemingly routine marketing content can contribute to attacker reconnaissance. It explores both the information explicitly disclosed by the case study and the additional intelligence that can be derived from vendor-documented integration capabilities, illustrating how public technology disclosures can assist target profiling, technology identification, and future reconnaissance efforts.

## Analysis of Ernst & Young ServiceNow Case Study[^1]
[^1]: *Source:  
ServiceNow — [“EY puts people first with responsible AI”](https://www.servicenow.com/customers/ey-ai.html)   
(accessed September 25, 2026).*

The ServiceNow website features a case study that showcases how EY uses AI across its ServiceNow environment. Because vendor case studies are intended as advertising, they often publicly disclose operational details about technologies, workflows, and business processes. This case study reveals that EY uses the IT Service Management (ITSM), IT Operations Management (ITOM), and HR Service Delivery modules; that EY runs a massive, global operation; and that EY is an early adopter of AI and new ServiceNow features, including agentic automation.

In addition to the information the case study explicitly discloses, it includes links to the product pages for the listed modules. These product pages highlight key integrations across Cloud & Infrastructure, Security Stack, and Business Systems management. Further exploration of the ServiceNow website's full list of integrations reveals extensive capabilities spanning numerous high-value products.

The publicly available information on ServiceNow's website provides intelligence that can reduce uncertainty during reconnaissance, target selection, and further investigation of the environment. The combination of specific modules and integrations helps identify systems that may contain sensitive or business-critical data and allows attackers to focus research on known vulnerabilities. Additionally, EY’s scale and early‑adopter approach to AI indicate heightened exposure to zero‑day vulnerabilities, making these disclosures particularly valuable during reconnaissance.

### Information Gained from Case Study Disclosures
Case study disclosures provide attackers with significant operational insight.

 - At the bottom of the case study, an "About EY" section discloses that "teams in more than 150 countries work across a full spectrum of services in assurance, consulting, tax, strategy and transactions."
	 - This signals to a threat actor that EY operates across numerous regulated domains and handles substantial volumes of sensitive data.
 - The case study reveals that EY has 400,000 employees and that more than 16,000 of those employees are technology professionals using the ServiceNow AI Platform. Additionally, it states that "the service desk handles more than a million tickets annually, delivering support in 21 languages across 30 service desks."
	 - These details show an attacker that EY maintains a large, complex environment with many potential points of entry.
	 - The scale and diversity of employees suggest that social engineering attempts would likely find a foothold.
- The article identifies the specific modules EY uses, including the AI Platform, ITSM, ITOM, HRSD, and AI Agents.
	- The combination of these modules indicates that EY relies on extensive centralized and automated workflows, which introduce predictability and may expand the organization's potential attack surface.
	- Knowledge of the modules being used allows an attacker to focus research on known vulnerabilities.
- The case study further describes EY's workflows, including that ServiceNow is used for password resets; HR compliance, benefits, and time-off requests; AI-guided workflows for HR and IT; and AI-generated resolution notes and knowledge base articles.
	- These disclosures highlight two clear targets:
		- HR compliance and benefits workflows contain sensitive information.
		- Password-reset workflows may be of particular interest to attackers because of their relationship to identity and access management processes.
- The case study emphasizes EY's use of ServiceNow's AI features and notes that AI agents perform 12,000 actions per day.
	- Heavy reliance on AI agents suggests predictable automation behavior and potential opportunities for poisoning or manipulation.
- The case study states that EY aims "to stay on the leading edge of the fast-evolving world of agentic AI" and is an early adopter of new ServiceNow features.
	- This signals to an attacker that EY may have increased exposure to zero-day vulnerabilities, unstable features, and immature security controls.

The information in the case study suggests that ServiceNow occupies a highly centralized role across multiple business functions, making it a potentially valuable reconnaissance target and operational pivot point.

### Information Gained from Integrations[^2]
[^2]: *Sources:  
[IT Service Management (ITSM) - ServiceNow  ](https://www.servicenow.com/products/itsm.html)   
[ITOM - Enterprise IT Operations Management - ServiceNow](https://www.servicenow.com/products/it-operations-management.html)    
[HR Service Delivery - HR Management - ServiceNow](https://www.servicenow.com/products/hr-service-delivery.html)   
[ServiceNow AI Platform - ServiceNow](https://www.servicenow.com/platform.html)    
[Integrations - ServiceNow Store](https://store.servicenow.com/store/apps?g=integrations)    
(Accessed September 25, 2026).*

Links in the case study lead to the product pages for each listed module. These product pages include diagrams showing the major integrations for each product. This publicly available information exposes potential operational dependencies and attack pathways. Further navigation to the full list of product integrations reveals support for integrations across a wide range of services.

#### Identity & Access Management (IAM)
Identity and access management integrations centralize authentication, provisioning, and account lifecycle workflows. When these products are integrated, identity changes and access operations flow through ServiceNow.

Key identity and access management integrations available include:

 - **Identity Providers:**
	 - Microsoft Entra ID (Azure AD)
	 - Okta
	 - Oracle Cloud IAM
	 - Ping Identity
- **Identity Governance and Provisioning:**
	- SailPoint
	- Saviynt
	- Oracle Access Governance
- **Authoritative Lifecycle Sources:**
	- Workday
	- SAP SuccessFactors
	- Oracle HCM Cloud
	- ADP
	- UKG

Even without knowing which integrations are deployed, the supported capabilities reveal the types of identity systems that may be connected to ServiceNow, enabling an attacker to narrow the list of potential IAM applications in the organization's environment.

#### Privileged Access Management (PAM)
Privileged Access Management (PAM) integrations govern access to administrative accounts, privileged credentials, and elevated permissions. When integrated with ServiceNow, privileged access requests, approvals, and governance workflows may be coordinated through a centralized platform.

Key privileged access management integrations available include:

 - **Core PAM Platforms**
	 - CyberArk
	 - BeyondTrust
 - **Privileged Access Dependencies**
	 - AWS
	 - Microsoft Azure
	 - Google Cloud Platform
	 - Kubernetes
	 - Terraform
	 - GitHub, GitLab, Bitbucket

These integrations suggest that ServiceNow may play a role in managing or coordinating privileged access workflows. This allows an attacker to identify likely administrative control points, understand where elevated access may be governed, and prioritize reconnaissance against systems that can provide broad operational influence across the enterprise.

#### HR, Payroll & Workforce
HR, payroll, and workforce management integrations centralize employee information, organizational hierarchy, payroll data, and workforce lifecycle processes. When integrated with ServiceNow, these systems can automate onboarding, offboarding, employee changes, benefits administration, and HR service delivery workflows.

Key HR, payroll, and workforce integrations available include:

 - **Human Capital Management (HCM)**
	 - Workday
	 - SAP SuccessFactors
	 - Oracle HCM Cloud
- **Payroll & Workforce Management**
	- ADP
	- UKG

Support for these integrations indicates that ServiceNow can be connected to systems that contain employee, organizational, and workforce lifecycle data. This helps an attacker understand how personnel information and employee-driven business processes may flow throughout the enterprise.

#### Security & Threat Management
Security and threat management integrations aggregate security telemetry, alerts, incidents, and threat intelligence from across the environment. When integrated with ServiceNow, these products enable centralized security operations workflows and provide visibility into security events occurring throughout the enterprise.

Key security and threat management integrations available include:

 - **Security Information & Event Management (SIEM)**
	 - Splunk
	 - Microsoft Sentinel
	 - IBM QRadar
 - **Endpoint Detection & Response (EDR)/Extended Detection & Response (XDR)**
	 - Microsoft Defender
	 - CrowdStrike
	 - Carbon Black
 - **Security Operations & Threat Management**
	 - Rapid7
	 - Cisco SecureX
 - **Network Security**
	 - Palo Alto Networks
- **Security Monitoring & Observability**
	- Splunk ITSI
	- Datadog
	- Dynatrace
	- LogicMonitor
	- New Relic

These integrations provide insight into the organization's likely security operations architecture, enabling an attacker to better understand how security events are detected, aggregated, investigated, and managed throughout the environment.

#### Assets, Infrastructure & Operations

Asset, infrastructure, and operations integrations provide visibility into enterprise systems, cloud resources, network infrastructure, configuration management, and operational workflows. When integrated with ServiceNow, these products support asset discovery, infrastructure monitoring, configuration management, operational automation, and service management processes.

Key asset, infrastructure, and operations integrations available include:

-   **IT Service Management & Operations**
    -   Jira
    -   BMC Remedy
-   **Infrastructure Monitoring & Observability**    
    -   SolarWinds
    -   Datadog
    -   Dynatrace
    -   LogicMonitor
    -   New Relic
    -   Microsoft System Center Operations Manager (SCOM)
-   **Network & Infrastructure Management**    
    -   Cisco Meraki
    -   Infoblox
    -   F5 Networks
-   **Cloud & Infrastructure Platforms**    
    -   AWS
    -   Microsoft Azure
    -   Google Cloud Platform
    -   Kubernetes
-   **Infrastructure Automation**    
    -   Terraform
    -   Ansible
    -   Puppet
    -   Chef

The availability of these integrations highlights the types of systems that may be used to manage, monitor, automate, and inventory enterprise infrastructure, helping an attacker identify likely sources of asset, network, cloud, and operational intelligence to inform future reconnaissance.

#### Vulnerability & Compliance
Vulnerability and compliance integrations provide visibility into security weaknesses, compliance requirements, remediation activities, and risk-management processes. When integrated with ServiceNow, these products can support vulnerability tracking, risk assessments, compliance monitoring, and remediation workflow automation.

Key vulnerability and compliance integrations available include:

-   **Vulnerability Management**   
    -   Rapid7
    -   Tenable
    -   Qualys
-   **Compliance & Risk Management**    
    -   ServiceNow Governance, Risk, and Compliance (GRC)
    -   Oracle Access Governance
    -   SailPoint
    -   Saviynt
-   **Security & Exposure Analytics**    
    -   Microsoft Defender
    -   CrowdStrike
    -   Palo Alto Networks

These supported integrations reveal the types of systems that may be used to identify, prioritize, track, and remediate security weaknesses, helping an attacker understand how vulnerabilities, compliance requirements, and security risks may be managed across the enterprise.

#### Incident Response & Support
Incident response and support integrations facilitate the intake, coordination, tracking, and resolution of security incidents, operational issues, service requests, and customer support activities. When integrated with ServiceNow, these platforms can centralize ticketing, case management, escalation workflows, collaboration, and response activities across multiple teams.

Key incident response and support integrations available include:

-   **Service Management & Ticketing**    
    -   Jira Service Management
    -   BMC Remedy
    -   Zendesk
    -   Freshdesk
-   **Collaboration & Communications**    
    -   Microsoft Teams
    -   Slack
    -   Zoom
    -   Webex
-   **Customer Relationship & Support Platforms**    
    -   Salesforce
-   **Communications & Notifications**    
    -   Twilio
    -   Vonage
    -   SendGrid

The availability of these integrations provides insight into the types of platforms that may be used to coordinate support operations, manage incidents, facilitate communication, and track remediation activities, helping an attacker understand how issues are likely to be escalated, communicated, and resolved throughout the organization.

#### Third-Party & API-Driven Integrations

Third-party and API-driven integrations extend ServiceNow beyond its native capabilities by connecting it to external applications, data sources, automation platforms, and business systems. When integrated with ServiceNow, these products enable data exchange, workflow orchestration, process automation, and cross-platform operations.

Key third-party and API-driven integrations available include:

-   **Business & Enterprise Applications**
    
    -   Salesforce
    -   Microsoft Dynamics 365
    -   SAP
    -   Oracle EBS / Oracle Cloud ERP
    -   Google Workspace
    -   Microsoft 365
    -   Dropbox
-   **Finance & Procurement**
    
    -   Coupa
    -   SAP Ariba
    -   Workday Financials
    -   NetSuite
-   **Databases & Data Platforms**
    
    -   MySQL
    -   PostgreSQL
    -   SQL Server
    -   Oracle DB
    -   MongoDB
    -   Snowflake
-   **Automation & Robotic Process Automation (RPA)**
    
    -   UiPath
    -   Automation Anywhere
    -   Blue Prism
    -   Microsoft Power Automate

Support for third-party and API-driven integrations demonstrates ServiceNow's ability to exchange information and automate processes across a broad ecosystem of external platforms. This provides an attacker with information about the types of business systems, data repositories, and automation technologies that may be connected through ServiceNow, helping identify potential dependencies, data flows, and areas for future reconnaissance.

Collectively, the integration capabilities demonstrate ServiceNow's potential role as a centralized platform connecting identity services, workforce systems, security operations, infrastructure management, enterprise applications, and business processes. Even without knowledge of EY's specific implementation, the publicly documented integration ecosystem reduces uncertainty about which technologies may interact with the platform, enabling an attacker to build a more informed model of the organization's potential operational dependencies and to prioritize future reconnaissance accordingly. 

### Reconnaissance Value of ServiceNow Case Study Disclosures

Taken together, the case study disclosures and published integration capabilities provide a broader view of how ServiceNow may function within an enterprise environment.

The value of the case study extends beyond identifying the ServiceNow modules used by EY. When combined with publicly documented integration capabilities, the disclosures help an attacker understand how ServiceNow may fit within the broader enterprise architecture. The case study reveals the platform's role in IT, HR, and automation workflows, while the integration ecosystem demonstrates ServiceNow's ability to interact with identity providers, security tools, cloud platforms, business applications, and operational systems. Even without confirmation of specific integrations, this information enables attackers to reduce uncertainty, identify likely technology dependencies, and prioritize future reconnaissance against systems that may be connected to a centralized operational hub.

## Vendor Case Studies as a Reconnaissance Starting Point

Vendor case studies are particularly valuable during reconnaissance because they provide information that organizations rarely disclose elsewhere in such a consolidated and accessible format. Unlike technical documentation, vulnerability disclosures, or job postings, case studies are designed to publicly showcase how products are used in real-world environments. As a result, they often reveal specific technologies, business processes, organizational priorities, and operational dependencies.

From an attacker's perspective, case studies help to refine target selection. Rather than starting with a large number of unknowns, an attacker can use case study disclosures to identify technologies in use, understand how those technologies support business operations, and prioritize areas for further investigation. This allows reconnaissance efforts to become more targeted and efficient.

Case studies are particularly valuable because they frequently disclose:

-   Specific products, modules, and features deployed within an environment.
-   Business processes supported by those technologies.
-   Organizational scale, geographic footprint, and operational complexity.
-   Digital transformation initiatives and strategic technology priorities.
-   Automation, AI, and emerging technology adoption.
-   Integration points between platforms and business systems.
-   Operational dependencies that may create high-value targets or single points of failure.

When these disclosures are combined with publicly available vendor documentation, product integration catalogs, technical blogs, job postings, and vulnerability databases, attackers can develop a more complete understanding of an organization's likely technology ecosystem without interacting directly with the target.

The EY ServiceNow case study demonstrates how a seemingly routine marketing artifact can provide meaningful intelligence. The case study identifies specific ServiceNow modules, describes operational workflows, highlights the organization's scale, and reveals the use of AI-driven automation. Publicly available integration documentation then expands that picture by illustrating the types of systems that may connect to the platform. Together, these disclosures provide a foundation for subsequent reconnaissance and help an attacker build a more informed model of the organization's potential technology landscape.

In this way, vendor case studies function as reconnaissance starting points rather than standalone intelligence sources. Their value lies not only in the information they directly disclose, but also in their ability to guide and refine future investigation across a much broader attack surface.

## Implications & Considerations

The EY case study demonstrates how seemingly benign marketing content can provide meaningful intelligence when viewed through the lens of attacker reconnaissance. While the case study does not disclose sensitive technical details, it reveals information about technologies in use, operational workflows, organizational scale, and business priorities. When combined with publicly available vendor documentation, this information becomes significantly more valuable than any individual disclosure alone.

A key consideration is that attackers rarely rely on a single source of information. Instead, they aggregate intelligence from multiple public sources, including vendor case studies, product documentation, integration catalogs, job postings, conference presentations, professional networking sites, patent filings, and vulnerability databases. Each source may reveal only a small piece of information, but together they develop a more complete picture of a target environment.

This creates a disconnect between how organizations often evaluate disclosures and how attackers consume them. Individual disclosures may appear harmless when reviewed independently, yet those same disclosures can become operationally significant when correlated with other publicly available information. Technologies, workflows, integrations, and organizational details that may seem unrelated from a business or marketing perspective can collectively reveal architectural dependencies, operational processes, and potential attack paths.

The challenge for organizations is balancing the business value of public-facing content against the intelligence value it provides to adversaries. Vendor case studies can promote innovation, strengthen customer relationships, and demonstrate technical capabilities. However, they can also reveal information that assists target selection, promotes focused vulnerability research, and enables attackers to prioritize future reconnaissance activities.

Organizations should therefore assess public technology disclosures not only for the information they explicitly reveal, but also for what can reasonably be inferred when combined with other publicly available sources. Security reviews should consider how disclosed technologies, business processes, integrations, and operational details contribute to the organization's broader public technology footprint and whether those disclosures collectively provide attackers with a clearer understanding of the environment than intended.

## Conclusion

The intelligence value of vendor case studies lies not in any single disclosure, but in their ability to reduce uncertainty about technologies, processes, integrations, and operational dependencies. While individual disclosures may appear harmless, the EY ServiceNow case study demonstrates how publicly available information can be combined with vendor documentation to build a more complete understanding of a target environment and guide future reconnaissance activities.

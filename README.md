# Cloud-Native SIEM with Azure Monitor & Microsoft Sentinel

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-0078D4?logo=microsoftazure&logoColor=white)
![Sentinel](https://img.shields.io/badge/SIEM%20%2F%20SOAR-Microsoft%20Sentinel-5E5E5E)
![KQL](https://img.shields.io/badge/Query%20Language-KQL-blue)
![ISO 27001](https://img.shields.io/badge/Compliance-ISO%2FIEC%2027001%3A2022-green)
![Status](https://img.shields.io/badge/Environment-Azure%20Sandbox-orange)

> End-of-internship project carried out at **SMARTOVATE LTD** (June – July 2026, 8 weeks): design and deployment of a centralized, cloud-native security monitoring solution, from log collection to automated incident response.

---

## Table of contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Technology choices](#technology-choices)
- [ISO/IEC 27001:2022 compliance](#isoiec-270012022-compliance)
- [Tech stack](#tech-stack)
- [Author](#author)

---

## Overview

Cloud adoption has dissolved the traditional network perimeter: identities have become the main control point and log volumes keep growing. This project builds a **Cloud-Native SIEM** on the Microsoft Azure ecosystem that:

1. **Centralizes** logs in a Log Analytics workspace (via Azure Monitor),
2. **Detects** suspicious activity in near real time with KQL analytics rules in Microsoft Sentinel,
3. **Visualizes** the security posture through interactive Workbooks,
4. **Automates** incident response with SOAR Playbooks built on Azure Logic Apps,
5. **Assesses** the architecture against ISO/IEC 27001:2022 controls.

Everything was built and tested in an **isolated Azure sandbox**; no production environment was touched.


## Architecture

The solution is organized in four sequential layers:

| Layer | Components | Role |
|-------|------------|------|
| **Collection & ingestion** | Azure Monitor, Log Analytics Workspace | Aggregate logs and metrics from Entra ID, Azure Activity, Office 365, VMs and Azure Firewall |
| **Analysis & detection** | Microsoft Sentinel, KQL Analytics Rules, Threat Intelligence, Watchlists | Correlate events, detect threats, reduce false positives, create incidents |
| **Visualization & reporting** | Sentinel Workbooks | KPIs, trends, failed sign-ins, geographic map |
| **Automation & remediation** | Logic Apps, Automation Rules, Microsoft Teams, Microsoft Graph | Notify the SOC, revoke sessions, disable compromised accounts, trace actions |

**Data flow:** Azure sources → Azure Monitor → Log Analytics → Sentinel rules → incidents → Workbooks / Automation Rules → Logic Apps playbooks.

The UML diagrams (use cases, class/domain models, sequence diagrams) and the C4 container/component diagram are available in the diagrams folder 

## Technology choices

| Layer | Selected | Alternatives considered |
|-------|----------|-------------------------|
| Collection & storage | Azure Monitor + Log Analytics | Elastic Agent, Splunk Forwarder, standalone Syslog agents |
| SIEM | Microsoft Sentinel | Splunk ES, IBM QRadar, Elastic Security |
| Visualization | Sentinel Workbooks | Grafana, Power BI |
| SOAR | Azure Logic Apps | Azure Functions, scheduled PowerShell, third-party SOAR |
| Identity & access | Entra ID + Azure RBAC | Local accounts, external directories |

Selection criteria: native Azure integration, coverage of SIEM/SOAR needs, simplicity within a two-month internship, and cost control in a test environment. The full comparison is in the technology justification document.


## ISO/IEC 27001:2022 compliance

The architecture was mapped to Annex A controls, including:

| Area | Controls |
|------|----------|
| Logging & monitoring | 8.15, 8.16, 8.6 |
| Incident management | 5.24, 5.25, 5.26, 5.28 |
| Threat intelligence | 5.7 |
| Identity & access | 5.15, 5.16, 5.18, 8.2 |
| Cloud services | 5.23 |
| Performance evaluation | 9.1, 5.35 |
| Environment separation | 8.31 |

**Result:** strong technical alignment. Gaps to close before production: formalized incident procedures and responsibilities, a documented cloud usage policy (5.23), log retention aligned with legal requirements (currently 30 days), formal test/production separation, and richer detection scenarios.


## Tech stack

Microsoft Azure · Azure Monitor · Log Analytics · Microsoft Sentinel · Microsoft Entra ID · Azure Logic Apps · Microsoft Graph API · KQL · Azure RBAC · Jira · UML / C4

## Author

Internship project at **SMARTOVATE LTD**, June – July 2026.

Wala Hassine 
Faculty of Sciences Monastir

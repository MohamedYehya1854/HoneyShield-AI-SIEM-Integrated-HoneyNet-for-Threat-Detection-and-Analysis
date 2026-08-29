# HoneyShield 🍯🛡️ 

### SIEM-Integrated HoneyNet for Threat Detection and Analysis

> **A proactive deception-based cybersecurity framework that combines Honeypots, SIEM, EDR, and network security controls to detect, analyze, and investigate cyber threats in a simulated enterprise environment.**

---

## 📌 Overview

**HoneyShield** is a deception-based cybersecurity framework designed to improve threat detection and analysis by integrating a distributed **HoneyNet** with centralized **SIEM** and **EDR** capabilities.

Instead of relying exclusively on traditional signature- and rule-based security controls, HoneyShield intentionally exposes controlled decoy services to attract attackers and capture high-fidelity information about their activities.

The collected telemetry is aggregated and analyzed through **T-Pot and the ELK Stack**, then integrated with **Wazuh** to provide centralized monitoring, event correlation, endpoint visibility, alerting, and incident investigation.

The project was developed as a **Bachelor of Science in Information Technology graduation project at the Faculty of Computers and Information, Mansoura University, 2025–2026**.

---

## 🎯 Project Objectives

HoneyShield was designed to:

* 🔍 Improve detection of known and unknown cyber threats.
* 🍯 Deploy multiple heterogeneous honeypot sensors through **T-Pot**.
* 📊 Centralize and visualize security events and attacker activity.
* 🔗 Correlate honeypot events with network and endpoint telemetry.
* 🖥️ Provide endpoint visibility through **Wazuh EDR**.
* 🚨 Generate high-confidence security alerts.
* 🧠 Transform attacker behavior into actionable threat intelligence.
* 🌐 Simulate a realistic enterprise network using **EVE-NG**.
* 🧪 Validate the architecture through controlled penetration-testing scenarios.

These objectives follow the project's documented functional scope, including real-time interaction capture, centralized log aggregation, SIEM forwarding, event correlation, dashboards, and systematic security testing.

---

## 🏗️ Architecture

HoneyShield follows a layered security architecture:

```text
                         ┌─────────────────────┐
                         │   External Network  │
                         │      / Attacker     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    ISP / Router     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │  FortiGate Firewall │
                         │ Web Filter │ IPS │ AV│
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┴───────────────┐
                    │                               │
                    ▼                               ▼
          ┌──────────────────┐             ┌──────────────────┐
          │   HoneyNet       │             │   Enterprise     │
          │     T-Pot        │             │    Endpoints     │
          ├──────────────────┤             ├──────────────────┤
          │ Cowrie           │             │ Windows          │
          │ Dionaea          │             │ Linux            │
          │ Conpot           │             │ Wazuh Agents     │
          │ Other Sensors    │             └────────┬─────────┘
          └────────┬─────────┘                      │
                   │                                │
                   ▼                                ▼
          ┌──────────────────┐             ┌──────────────────┐
          │   ELK Stack      │             │   Wazuh EDR      │
          │ Elasticsearch    │             │ Endpoint         │
          │ Logstash         │             │ Monitoring       │
          │ Kibana           │             └────────┬─────────┘
          └────────┬─────────┘                      │
                   │                                │
                   └──────────────┬─────────────────┘
                                  ▼
                       ┌─────────────────────┐
                       │     Wazuh SIEM      │
                       │ Correlation & Alert │
                       └──────────┬──────────┘
                                  │
                    ┌─────────────┼─────────────┐
                    ▼             ▼             ▼
               Dashboards      Alerts      Incident Reports
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Bee AI-SOC      │
                         │ Assistant       │
                         └─────────────────┘
```

The architecture separates **network security, deception, analytics, security operations, and endpoint monitoring**, allowing telemetry from each layer to feed into the next.

---

## 🔥 Core Components

### 🍯 T-Pot HoneyNet

**T-Pot** serves as the core deception platform and hosts multiple containerized honeypot sensors.

The project uses sensors including:

* **Cowrie** — SSH/Telnet interaction monitoring.
* **Dionaea** — Malware and malicious payload collection.
* **Conpot** — ICS/SCADA and industrial protocol deception.

T-Pot also provides centralized logging and visualization through its integrated ELK stack.

### 🛡️ FortiGate

**FortiGate Firewall** provides the primary network security layer, including:

* Network perimeter protection
* Access control
* Traffic filtering
* Web filtering
* Intrusion Prevention System (IPS)
* Antivirus inspection

### 📊 Wazuh SIEM

Wazuh acts as the centralized security monitoring and correlation platform.

It provides:

* Security event collection
* Log analysis
* Event correlation
* Alert generation
* Security dashboards
* Threat investigation

### 🖥️ Wazuh EDR

The endpoint layer provides host-level visibility through Wazuh agents.

Telemetry includes:

* Process execution
* File-system activity
* Endpoint events
* Suspicious behavioral activity

This enables endpoint telemetry to be correlated with network and honeypot events.

### 🐝 Bee AI-SOC Assistant

HoneyShield also includes the **Bee AI-SOC Assistant**, with:

* API configuration
* SOC dashboard
* Alert-log visualization
* AI-assisted security analysis
* Incident Response reports

The implementation also includes Slack-based alerting and cloud log/telemetry archiving.

---

## 🧰 Technology Stack

| Category                 | Technologies                        |
| ------------------------ | ----------------------------------- |
| Network Emulation        | **EVE-NG**                          |
| Virtualization           | **VMware Workstation**              |
| Firewall                 | **FortiGate v7.6**                  |
| SIEM                     | **Wazuh**                           |
| EDR                      | **Wazuh**                           |
| Honeypot Platform        | **T-Pot**                           |
| Honeypot Sensors         | **Cowrie, Dionaea, Conpot**         |
| Analytics                | **Elasticsearch, Logstash, Kibana** |
| Containers               | **Docker**                          |
| Servers                  | **Ubuntu Server**                   |
| Network Devices          | **Cisco Routers & Switches**        |
| Endpoints                | **Windows 10, Linux Slax**          |
| Attacker Environment     | **Kali Linux 2025**                 |
| Traffic Analysis         | **Wireshark**                       |
| Network Scanning         | **Nmap**                            |
| Web Exploitation Testing | **SQLMap**                          |
| Exploitation             | **Metasploit Framework**            |
| Enumeration              | **enum4linux, dnsenum, SNMP tools** |

The project documentation identifies EVE-NG, VMware, FortiGate, Wazuh, T-Pot, Docker, Ubuntu, Cisco networking equipment, Windows/Linux endpoints, and Kali Linux as core implementation technologies.

---

## 🔄 How HoneyShield Works

### 1️⃣ Traffic Entry

External traffic enters the simulated enterprise environment through the ISP/router layer.

### 2️⃣ Perimeter Inspection

FortiGate applies security controls such as:

* Web Filtering
* IPS
* Antivirus
* Firewall policies

### 3️⃣ Deception

Suspicious traffic destined for the deception environment is redirected toward the **T-Pot HoneyNet**.

### 4️⃣ Attack Capture

Honeypot sensors capture attacker interactions, commands, scans, exploitation attempts, and malicious payloads.

### 5️⃣ Data Processing

T-Pot processes and visualizes the collected telemetry through:

**Logstash → Elasticsearch → Kibana**

### 6️⃣ SIEM Correlation

Security events are forwarded to **Wazuh**, where honeypot telemetry can be correlated with network and endpoint events.

### 7️⃣ Endpoint Visibility

Wazuh agents provide additional endpoint-level telemetry through the EDR layer.

### 8️⃣ Alerting & Investigation

Correlated events generate alerts and can be surfaced through dashboards, Slack notifications, the Bee AI-SOC Assistant, and incident-response reports.

This end-to-end flow is a core part of the HoneyShield design, connecting T-Pot telemetry with network, SIEM, and endpoint data.

---

## 🧪 Security Testing

HoneyShield was evaluated using a **before-and-after testing methodology**.

### Phase 1 — Before Security Implementation

The environment was tested without the HoneyNet and SIEM-based security solution to establish a baseline.

Attack scenarios included:

* SQL Injection
* Web exploitation
* Remote Code Execution
* Privilege escalation

The documented baseline showed that these attacks could succeed without generating security alerts.

### Phase 2 — After HoneyShield Deployment

The complete security architecture was deployed and tested against controlled attack scenarios.

Testing focused on:

* Detection capability
* Event correlation
* Honeypot visibility
* Endpoint monitoring
* Alert generation
* Attack lifecycle visibility
* Overall security pipeline effectiveness

The project used penetration-testing tools such as **Nmap, SQLMap, Metasploit, Hydra, and other enumeration tools** during controlled evaluation.

---

## 📈 Key Capabilities

### 🔍 High-Confidence Detection

Honeypots have no legitimate business purpose, meaning interactions with them are inherently suspicious and can provide high-confidence security signals.

### 🧠 Threat Intelligence

HoneyShield captures attacker behavior, tools, commands, techniques, and exploitation activity to support threat analysis.

### 🔗 Centralized Correlation

Instead of analyzing honeypot logs independently, HoneyShield correlates deception telemetry with network and endpoint events.

### 📊 Real-Time Visibility

Security analysts can monitor attacks through Wazuh and T-Pot dashboards.

### 🧩 Modular Architecture

The architecture separates major security functions, allowing components to be managed and extended independently.

### 🛡️ Defense in Depth

HoneyShield combines:

**Firewall + IPS + Honeypots + SIEM + EDR + Monitoring + Alerting**

into one coordinated security framework.

---

## 📂 Repository Structure

A recommended repository structure for the implementation is:

```text
HoneyShield/
│
├── README.md
│
├── docs/
│   ├── architecture/
│   ├── network-topology/
│   ├── deployment/
│   ├── testing/
│   └── reports/
│
├── fortigate/
│   ├── firewall-policies/
│   ├── web-filter/
│   ├── ips/
│   └── antivirus/
│
├── tpot/
│   ├── sensors/
│   ├── logging/
│   └── dashboards/
│
├── wazuh/
│   ├── rules/
│   ├── agents/
│   ├── integrations/
│   └── dashboards/
│
├── bee-ai-soc/
│   ├── api/
│   ├── frontend/
│   └── reports/
│
├── scripts/
│   ├── deployment/
│   ├── testing/
│   └── integrations/
│
├── tests/
│   ├── reconnaissance/
│   ├── exploitation/
│   └── detection/
│
└── LICENSE
```

> **Note:** This structure is a recommended GitHub organization based on the components documented in the project. Adapt it to match the actual files committed to the repository.

---

## 🖥️ Monitoring & Dashboards

HoneyShield provides multiple monitoring views, including:

* **Wazuh SIEM Dashboard**
* **Connected Endpoints Dashboard**
* **T-Pot Kibana Dashboard**
* **T-Pot Elastic Dashboard**
* **Bee AI-SOC Assistant Dashboard**
* **Incident Response Reports**

These dashboards provide visibility into security events, connected endpoints, honeypot activity, and attack behavior.

---

## ⚠️ Limitations

HoneyShield is a **proof-of-concept academic deployment**, so its results should be interpreted within the scope of the simulated environment.

Current limitations include:

* Testing was performed in a simulated enterprise environment.
* Advanced APT and insider-threat scenarios were not extensively evaluated.
* Automated SOAR-level containment was not implemented.
* High-volume scalability testing was limited.
* Honeypot configurations remain largely static.
* The collected traffic represents controlled attack scenarios rather than unrestricted Internet traffic.

---

## 🚀 Future Work

Future development directions include:

* 🤖 Machine-learning-based behavioral analysis
* ⚙️ SOAR integration and automated containment
* 🍯 Adaptive honeypot behavior
* 🧪 More advanced APT and multi-stage attack scenarios
* 📈 Large-scale performance and scalability testing
* 🧠 Improved AI-assisted SOC investigation
* 🌐 More realistic and distributed deception environments

These directions are explicitly identified in the project's future-improvement section.

---

## 👥 Project Team

**Faculty of Computers and Information — Mansoura University**
**Information Technology Department**

### Team Members

* Amin Fakhr Eldin Ahmed
* Saif El-Din Bedair Ali
* Abdulrahman Mohamed Fayad
* Amr Khaled Abdallah
* Mohamed Ahmed Abdelhalim
* Mohamed Ahmed Abdallah
* Mohamed Al-Sayed Al-Tantawy
* Mohamed Alaa Mokhtar
* Mohamed Awad Ali
* Mohamed Mahmoud Ramadan

### Supervisors

* **Dr. Heba Kandil**
* **Eng. Karam Mohamed**

---

## 🎓 Academic Project

This project was submitted in partial fulfillment of the requirements for the degree of:

**Bachelor of Science in Information Technology**
**Faculty of Computers and Information — Mansoura University**
**Academic Year 2025–2026**

---

## 🔐 Disclaimer

HoneyShield is an **academic cybersecurity research and testing project**.

All penetration testing and attack simulations described in this repository are intended for **authorized, isolated environments only**.

Do not use the included techniques or tools against systems, networks, or services without explicit authorization.

---

## ⭐ Acknowledgment

We would like to express our gratitude to our supervisors, **Dr. Heba Kandil** and **Eng. Karam Mohamed**, for their guidance, technical support, and continuous feedback throughout the project.

We also thank the **Faculty of Computers and Information, Mansoura University**, for providing the academic environment and resources required to complete this work.

---

<p align="center">

### 🛡️ HoneyShield

**From Deception to Defense.**

</p>

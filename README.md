# 🛡️ Building a Professional SOC Home Lab: Wazuh SIEM & Threat Detection

<img src="soc_dashboard_mockup_1773179635123.png" width="800" alt="SOC Banner">

## 🎯 Project Overview
This project documents the end-to-end deployment of a **Security Operations Center (SOC) home lab**. The goal was to establish a centralized monitoring system to detect, analyze, and respond to security threats across a virtualized network. This lab simulates a corporate environment with a SIEM manager, a Linux attack node, and a hardened Windows endpoint.

## 🛠️ Technology Stack
- **SIEM/SOAR**: Wazuh (Indexer, Server, Dashboard)
- **Endpoint Monitoring**: Wazuh Agent, Sysmon (Windows)
- **Virtualization**: Oracle VirtualBox
- **Attack Tools**: Kali Linux (Nmap, Hydra)
- **OS Environment**: Ubuntu Server 24.04 LTS, Windows 11 Home, Kali Linux 2024.x

## 🚀 Key Milestones & "The Win"

### 1. The SIEM "Brain" (Wazuh Manager)
I successfully deployed the Wazuh manager on a resource-constrained Ubuntu Server. I overcame significant hurdles, including:
- **Disk Partitioning**: Expanded a 12GB LVM partition to 50GB to handle high-volume logs.
- **Service Optimization**: Resolved port conflicts (1515/55000) and automated `needrestart` configurations for 24/7 uptime.

<img src="media__1773187751829.png" width="600" alt="Wazuh Dashboard Overview">

### 2. Windows Endpoint "X-Ray" Vision (Sysmon)
I integrated a Windows 11 endpoint with **Sysmon** to achieve deep process-level visibility. 
- **Achievement**: Detected suspicious DLL surrogate injections (`dllhost.exe`) and anomalous service hosts (`svchost.exe`).
- **Audit Compliance**: Performed a **CIS Benchmark** scan (SCA), identifying security misconfigurations against industry standards.

<img src="media__1773089838278.png" width="600" alt="Configuration Assessment Success">

### 3. Automated Incident Response (SOAR)
Configured **Active Response** to move from "Alerting" to "Protecting."
- **Attack Scenario**: A brute-force SMB attack was launched from Kali Linux using Hydra.
- **Response**: Upon detecting **Level 12** authentication failures, Wazuh automatically triggered a firewall block via `netsh.exe`, neutralizing the attack in 60 seconds.

<img src="automated_threat_block_concept_1773179650361.png" width="600" alt="Automated Threat Block Concept">  
<img src="media__1773187751373.png" width="600" alt="Automated Defense Triggered">

## 📊 Detection Portfolio (Key Alerts)
| Alert Level | Description | Tech Used |
| :--- | :--- | :--- |
| **Level 13** | Brute Force Attack detected on Windows | Wazuh Manager |
| **Level 12** | Suspicious Process (dllhost.exe) detected | Sysmon |
| **Level 3** | New Account Discovery (net.exe) | Windows Security Logs |
| **Active** | Automated Firewall Block (Rule 607) | Active Response |

<img src="media__1773092150378.png" width="600" alt="Golden Screenshot - Global Events">

## 💡 Lessons Learned
- **Persistence is the best tool**: Troubleshooting Hyper-V conflicts and VirtualBox "Critical Errors" taught me more about host-level security than any textbook.
- **Data is king**: A SIEM is only as good as the telemetry it receives; Sysmon is essential for true Windows visibility.

## 🖼️ Technical Gallery (The Journey)

Below is a collection of captures showcasing the evolution of the lab, from initial connectivity tests to full-scale attack simulation and detection.

| Description | Capture |
| :--- | :--- |
| **Initial Kali Scan Verification** | <img src="media__1773187751540.png" width="200"> |
| **Wazuh Agent Deployment Logs** | <img src="VirtualBox_kali_09_03_2026_22_34_33.png" width="200"> |
| **Windows Security Event Ingestion** | <img src="VirtualBox_Windows_11_10_03_2026_22_44_08.png" width="200"> |
| **Sysmon Process Monitoring (Deep Dive)** | <img src="VirtualBox_Windows_11_11_03_2026_00_03_00.png" width="200"> |
| **Active Response Configuration Check** | <img src="VirtualBox_Windows_11_11_03_2026_00_09_32.png" width="200"> |

---
*Developed by Opeyemi Benjamin — aspiring SOC Analyst.*

# AI-based APT Detection Lab (GCP-Based SOC Simulation)

## Overview
This lab simulates real-world Advanced Persistent Threat (APT) behavior in a cloud environment using Caldera and Atomic Red Team. It detects malicious activity using AI-powered techniques (Elastic ML, Splunk MLTK, Sentinel UEBA) and traditional detection engineering methods (Sigma, YARA, SPL, KQL). The environment is hosted on Google Cloud using Terraform.

## Key Features
- Simulate APT kill chains mapped to MITRE ATT&CK
- Detect threats using AI/ML and manual threat hunting
- Build and tune detection rules in multiple platforms (Splunk, Sentinel, Elastic)
- Collect and analyze endpoint and network telemetry (Velociraptor, Zeek, Suricata)
- Perform hands-on SOC analysis with custom Jupyter anomaly models
- Automate lab setup using Infrastructure as Code (Terraform)

---

## Tool Stack

**Simulation Tools**  
- Atomic Red Team  
- Caldera (MITRE)  

**Detection Engines**  
- Elastic Stack with ML jobs  
- Splunk + MLTK  
- Microsoft Sentinel UEBA  

**Detection Rules**  
- Sigma (converted to SPL, KQL, and YARA)  
- YARA for host-level IOC detection  

**Threat Hunting**  
- Velociraptor  
- Zeek (network telemetry)  
- Suricata (IDS/NSM)  

**Machine Learning**  
- Jupyter Notebook + Scikit-Learn  
- Splunk MLTK  
- Azure ML (optional)

---

## Lab Topology (Google Cloud VMs)

| VM Name           | Purpose                      | Image                  | Specs                   |
|------------------|------------------------------|------------------------|-------------------------|
| `redteam-vm`      | Kali Linux + Caldera + ART   | Debian/Kali Linux      | 2 vCPU, 4 GB RAM        |
| `victim-vm`       | Windows Server 2022 + Agent  | Windows Server 2022    | 2 vCPU, 8 GB RAM        |
| `siem-vm`         | Splunk or Elastic Stack      | Ubuntu 22.04           | 4 vCPU, 16 GB RAM       |
| `sensor-vm`       | Zeek, Suricata               | Ubuntu 22.04           | 2 vCPU, 4 GB RAM        |
| (Optional) `sentinel` | Azure Sentinel via Defender | Azure VM + Log Analytics | Cloud-native |

---

## MITRE ATT&CK Techniques (test-samples)

- T1059: Command and Scripting Interpreter  
- T1021: Remote Services (RDP, SMB)  
- T1003: Credential Dumping  
- T1086: PowerShell Abuse  
- T1041: Data Exfiltration  

---

## Repository Structure

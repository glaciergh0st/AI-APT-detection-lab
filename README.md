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

| VM Name       | Purpose                             | GCP Machine Type | Specs           |
|---------------|--------------------------------------|------------------|-----------------|
| redteam-vm    | Kali + Caldera + ART                 | e2-medium        | 2 vCPU, 4 GB RAM |
| victim-vm     | Windows Server + Velociraptor Agent  | e2-medium        | 2 vCPU, 4 GB RAM |
| siem-vm       | Splunk or Elastic Stack              | e2-standard-2    | 2 vCPU, 8 GB RAM |
| sensor-vm     | Zeek + Suricata                      | e2-medium        | 2 vCPU, 4 GB RAM |

---

## MITRE ATT&CK Techniques (test-samples)

- T1059: Command and Scripting Interpreter  
- T1021: Remote Services (RDP, SMB)  
- T1003: Credential Dumping  
- T1086: PowerShell Abuse  
- T1041: Data Exfiltration  

---

## Repository Structure

- `infra/` – Terraform config for GCP lab infrastructure
- `simulation/` – Caldera campaigns and Atomic Red Team scripts
- `detections/`
  - `sigma/` – Sigma rules for APT behaviors
  - `spl/` – SPL rules for Splunk
  - `kql/` – KQL rules for Sentinel
  - `yara/` – YARA host detection rules
- `notebooks/` – Jupyter notebooks for anomaly detection
- `hunts/` – Velociraptor queries, Zeek logs, PCAPs
- `reports/` – SOC reports, screenshots, documentation
- `images/` – Diagrams, dashboards, architecture

---

## Getting Started

### 1. Deploy Infrastructure in GCP

- Navigate to `infra/terraform-gcp/`
- Customize the `main.tf` file with your GCP project ID and VM specs
- Run the following commands:
   terraform init
   terraform apply

### 2. Install Tools on Each VM

- **Red Team VM**: Install Caldera and Atomic Red Team
- **Victim VM**: Deploy Velociraptor agent
- **SIEM VM**: Install either Splunk + MLTK or Elastic Stack with ML
- **Sensor VM**: Install Zeek and Suricata (using AF_PACKET or mirror)

### 3. Simulate Attacks

- Launch Caldera operation
- Use Atomic Red Team to simulate MITRE ATT&CK TTPs
- Simulate exfiltration, lateral movement, and credential dumping

### 4. Detect and Analyze

- Use Sigma → SPL or KQL rules to detect behaviors in logs
- Analyze anomalies using Elastic ML or Splunk MLTK
- Investigate endpoints with Velociraptor
- Analyze network data with Zeek and Suricata

### 5. Report Findings

- Save alerts, dashboards, and query results
- Document the attack timeline and detection quality
- Export and publish a SOC-style report  

## Example Use Cases
- Compare AI-based vs manual threat detection
- Evaluate anomaly models using known attacker behavior
- SOC analysts can learn how to implement real-world APT detections

## License

MIT License
  

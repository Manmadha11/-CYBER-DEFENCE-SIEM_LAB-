# Wazuh Detection Engineering Lab

Enterprise SIEM detection engineering lab focused on attack simulation, threat detection, log analysis, and automated incident response using Wazuh.

---

# Project Overview

This project demonstrates the design and implementation of a practical cyber defense lab environment used to simulate real-world attacks and validate SIEM detection capabilities.

The lab was developed to demonstrate real-world Security Operations Center (SOC) workflows including:

* Attack simulation
* Log collection
* Threat detection
* Detection engineering
* Incident response
* Active response automation

The environment is fully isolated using a host-only network to ensure safe testing without impacting external systems.

---

# Objectives

The primary objectives of this lab are:

* Build an enterprise-style SIEM environment
* Simulate real-world cyber attacks
* Validate log ingestion and detection pipelines
* Engineer custom Wazuh detection rules
* Implement automated incident response
* Analyze attacker behavior and system logs
* Develop practical blue team investigation skills

---

# Lab Architecture

The environment consists of three virtual machines operating within an isolated host-only network.

| Machine       | Role             | Purpose                                             |
| ------------- | ---------------- | --------------------------------------------------- |
| Kali Linux    | Attacker Machine | Attack simulation and reconnaissance                |
| Ubuntu Server | Victim Endpoint  | Monitored target system                             |
| Wazuh Server  | SIEM Platform    | Centralized log collection, detection, and alerting |

---

# Network Configuration

The lab uses a Host-Only Adapter configuration to create a fully isolated internal environment.

## Benefits of Isolation

* Safe attack simulation
* No external network exposure
* Controlled communication flow
* Reliable testing conditions

All systems operate within the same subnet to enable communication between attacker, victim, and SIEM infrastructure.

---

# Simulated Attacks

The following attacks were simulated during the project:

| Attack                   | Tool Used | Objective                           |
| ------------------------ | --------- | ----------------------------------- |
| SSH Brute Force          | Hydra     | Simulate credential attacks         |
| Network Reconnaissance   | Nmap      | Enumerate exposed services          |
| Reverse Shell Simulation | Netcat    | Simulate command execution activity |

---

# Attack Workflow

The project follows a complete attack lifecycle workflow:

```text
Reconnaissance
      ↓
Attack Simulation
      ↓
Log Generation
      ↓
SIEM Detection
      ↓
Custom Rule Engineering
      ↓
Incident Response
      ↓
Active Response Automation
```

---

# Log Collection Sources

The Ubuntu endpoint was configured to forward multiple log sources to the Wazuh SIEM platform.

## Monitored Logs

| Log Source           | Purpose                    |
| -------------------- | -------------------------- |
| /var/log/auth.log    | Authentication monitoring  |
| Journald Logs        | System activity monitoring |
| UFW Firewall Logs    | Firewall event analysis    |
| Active Response Logs | Response validation        |

---

# Detection Engineering

Custom Wazuh detection rules were created to improve visibility into attack activity.

## Custom Rules Implemented

| Rule ID | Detection Purpose                    |
| ------- | ------------------------------------ |
| 100001  | SSH Brute Force Detection            |
| 100102  | Reconnaissance / Port Scan Detection |
| 100103  | Reverse Shell / Execution Detection  |

The rules were designed to identify suspicious activity patterns and trigger high-severity alerts.

---

# Active Response Automation

Automated response mechanisms were implemented using:

* Wazuh Active Response
* Custom response scripts
* UFW firewall integration

## Response Capability

The environment was configured to:

* Automatically identify attacker IP addresses
* Trigger firewall-based mitigation
* Block malicious connections in real time

---

# Detection Validation

The SIEM platform successfully detected:

* Repeated SSH authentication failures
* Reconnaissance scanning behavior
* Suspicious network activity
* Firewall blocking events
* Authentication log anomalies

Detection validation was performed using both built-in and custom Wazuh rules.

---

# Incident Response Workflow

The project includes practical incident response validation covering:

* Threat identification
* Alert investigation
* IP-based containment
* Firewall mitigation
* Response verification
* Security impact analysis

---

# Technologies Used

| Technology    | Purpose                   |
| ------------- | ------------------------- |
| Wazuh         | SIEM & Detection Platform |
| Ubuntu Server | Monitored Endpoint        |
| Kali Linux    | Attack Simulation         |
| Hydra         | SSH Brute Force           |
| Nmap          | Network Reconnaissance    |
| Netcat        | Reverse Shell Simulation  |
| UFW           | Firewall Mitigation       |
| Linux Syslogs | Log Collection            |

---

# Project Structure

```text
00_Project-Summary/
01_Architecture/
02_Setup/
03_Attack_Surface/
04_Attack_Simulation/
05_Log_Collection/
06_SIEM_Detection/
07_Detection_Engineering/
08_Incident_Report/
09_Templates/
images/
```

---

# Key Skills Demonstrated

This project demonstrates practical experience in:

* SIEM Administration
* Detection Engineering
* Security Monitoring
* Log Analysis
* Linux Administration
* Threat Detection
* Incident Response
* Firewall Management
* Attack Simulation
* Security Operations
* Blue Team Workflows

---

# MITRE ATT&CK Mapping

| Technique ID | Technique                         |
| ------------ | --------------------------------- |
| T1110        | Brute Force                       |
| T1046        | Network Service Scanning          |
| T1059        | Command and Scripting Interpreter |

---

# Evidence Collection

The repository contains screenshots and validation evidence for:

* Attack execution
* SIEM alerts
* Authentication logs
* Firewall blocks
* Active response execution
* Detection validation
* Incident response workflows

---

# Challenges Encountered

Several real-world troubleshooting scenarios were encountered and resolved during setup and testing.

## Issues Resolved

* Agent registration conflicts
* Wazuh configuration errors
* Active response failures
* Firewall rule validation issues
* Incorrect IP extraction in scripts
* Service communication problems
* Detection rule tuning challenges

These troubleshooting experiences helped strengthen practical SOC and system administration skills.

---

# Learning Outcomes

This project provided hands-on experience with:

* Enterprise SIEM workflows
* Threat detection engineering
* Log correlation and analysis
* Active response implementation
* Real-world attack simulation
* Security event investigation
* Detection validation methodologies

---

# Future Improvements

Potential future enhancements include:

* Sysmon integration
* Windows endpoint monitoring
* Sigma rule conversion
* Threat intelligence integration
* Advanced detection correlation
* Dashboard customization
* EDR-style telemetry collection

---

# Conclusion

This project successfully demonstrates a complete enterprise-style cyber defense workflow using Wazuh.

The lab validates the ability to:

* Simulate attacks safely
* Collect and analyze logs
* Engineer custom detections
* Implement automated responses
* Investigate security events
* Perform practical SOC operations

This environment serves as a strong foundation for advanced detection engineering and incident response projects.

---

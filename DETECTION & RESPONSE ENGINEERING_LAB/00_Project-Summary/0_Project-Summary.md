# Cyber Defense Lab – Project Summary

### Attack Simulation, Detection & Incident Response using Wazuh

---

## 1. Overview

This project demonstrates a **Security Operations Center (SOC) simulation lab** designed to replicate real-world cyber attacks and validate detection capabilities using a SIEM platform.

The lab integrates attack simulation, log monitoring, detection engineering, and automated response within a controlled environment using **Wazuh SIEM**.

---

## 2. Objective

The primary objective of this project is to:

* Simulate real-world cyber attack scenarios
* Monitor system activity through centralized logging
* Detect malicious behavior using SIEM rules
* Implement automated response mechanisms
* Analyze and document security incidents

---

## 3. Lab Architecture

The environment consists of three virtual machines:

| Role     | System        | Purpose                                                      |
| -------- | ------------- | ------------------------------------------------------------ |
| Attacker | Kali Linux    | Simulate attacks (reconnaissance, brute force, exploitation) |
| Victim   | Ubuntu Server | Target system generating logs                                |
| SIEM     | Wazuh Server  | Centralized log collection, detection, and response          |

All systems operate within an isolated **host-only network** to ensure safe and controlled testing.

---

## 4. Attack Scenarios Simulated

The lab includes multiple attack techniques aligned with the MITRE ATT&CK framework:

| Attack Type      | Description                           | MITRE Technique |
| ---------------- | ------------------------------------- | --------------- |
| SSH Brute Force  | Multiple failed login attempts        | T1110           |
| Network Scanning | Port and service discovery using Nmap | T1046           |
| Reverse Shell    | Remote command execution              | T1059           |

---

## 5. Key Features

* End-to-end SOC workflow implementation
* Centralized log collection using Wazuh agent
* Custom detection rule creation
* MITRE ATT&CK mapping for alerts
* Active response using firewall-based blocking
* Real-time monitoring via Wazuh dashboard

---

## 6. Detection and Response Workflow

The project follows a structured detection pipeline:

1. Attacker initiates malicious activity
2. Target system generates logs
3. Wazuh agent collects and forwards logs
4. Wazuh manager analyzes events
5. Alerts are generated based on rules
6. Active response blocks malicious activity

---

## 7. Skills Demonstrated

This project highlights practical skills in:

* SOC operations and workflow understanding
* SIEM deployment and configuration
* Log analysis and monitoring
* Detection engineering and rule tuning
* Incident response implementation
* Troubleshooting and system debugging

---

## 8. Tools and Technologies

* Wazuh SIEM
* Kali Linux
* Ubuntu Server
* Nmap
* Netcat
* UFW Firewall

---

## 9. Key Outcomes

* Successfully simulated multiple attack scenarios
* Built and validated custom detection rules
* Implemented automated response mechanisms
* Developed hands-on experience in SOC operations
* Created a structured incident reporting workflow

---

## 10. Conclusion

This project demonstrates a practical implementation of a SOC environment, showcasing the ability to simulate attacks, detect threats, and respond effectively using SIEM tools.

It reflects real-world defensive security practices and provides a strong foundation for roles in **Security Operations and Threat Detection**.

---

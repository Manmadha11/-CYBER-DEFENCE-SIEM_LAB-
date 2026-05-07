# Cyber Defense Lab – Architecture Overview

### Attack Simulation, Detection & Incident Response using Wazuh

---

## 1. Project Overview

This project presents a **Security Operations Center (SOC) simulation lab** designed to replicate real-world cyber attack scenarios in a controlled and isolated environment.

The lab demonstrates how modern security teams:

* Simulate adversarial behavior
* Monitor system activity through centralized logging
* Detect threats using SIEM rules
* Respond to incidents in near real-time

The implementation uses **Wazuh SIEM** for log analysis, detection, and response automation.

---

## 2. Objective

The primary objective of this lab is to:

* Simulate realistic cyber attacks in a safe environment
* Validate detection capabilities using a SIEM platform
* Demonstrate end-to-end SOC workflow from attack to response

This lab is structured to build practical skills in:

* Lab architecture design
* Network configuration and isolation
* Attack simulation techniques
* Log collection and monitoring
* Detection engineering
* Incident response workflows

---

## 3. Lab Environment Description

The environment consists of three virtual machines configured within an isolated network to emulate a real-world enterprise scenario.

Each machine plays a specific role in the attack-defense lifecycle:

* The **attacker system** performs offensive operations
* The **victim system** generates logs and acts as a monitored endpoint
* The **SIEM server** collects, analyzes, and detects malicious activity

This setup enables controlled testing of detection and response mechanisms without external risk.

---

## 4. Machines in Scope

| Role     | System        | Description                                                                 |
| -------- | ------------- | --------------------------------------------------------------------------- |
| Attacker | Kali Linux    | Used to simulate reconnaissance, brute force, and command execution attacks |
| Victim   | Ubuntu Server | Target system running services and Wazuh agent for log forwarding           |
| SIEM     | Wazuh Server  | Centralized platform for log collection, detection, and alert generation    |

---

## 5. Network Architecture

The lab uses a **Host-Only network configuration** to ensure complete isolation from external networks.

### Key Characteristics

* Fully isolated environment
* No internet exposure
* Controlled and predictable traffic flow
* Safe execution of attack simulations

All machines are configured within the same subnet:

* Kali Linux: 192.168.239.101
* Ubuntu Server: 192.168.239.4
* Wazuh Server: 192.168.239.102

This allows seamless communication between attacker, victim, and SIEM components.

---

## 6. Architecture Validation

The environment was validated to ensure proper configuration before proceeding to attack simulation.

### Validation Steps

* Verified all virtual machines are powered on
* Confirmed network adapter configuration (Host-Only)
* Checked IP address assignment on each system
* Ensured all systems are within the same subnet
* Performed connectivity tests between all machines

---

## 7. Network Verification

Connectivity between systems was tested using ICMP (ping) to confirm proper communication.

Successful results indicate:

* Correct network configuration
* Functional routing within the lab
* Readiness for attack simulation and monitoring

---

## 8. Lab Validation Summary

The lab environment has been successfully configured and validated.

* All machines are reachable
* Network configuration is consistent
* Communication between systems is stable
* Infrastructure is ready for SIEM validation and attack simulation

---

## 9. Evidence Collection

Screenshots were captured to validate the setup and provide supporting evidence.

### Evidence Includes

* Virtual machines running
* Network adapter configuration
* IP address verification
* Connectivity test results

> **Note:** Store images inside the repository (e.g., `/images/`) and reference them using relative paths.

---

## 10. Conclusion

This phase establishes a fully functional and isolated cyber defense lab environment.

The infrastructure is now prepared for:

* SIEM service validation
* Attack simulation
* Detection engineering
* Incident response analysis

This foundation enables realistic SOC-level experimentation and learning.

---

## 11. Supporting Evidence

![VM Overview](../images/vm-overview.png)

![Wazuh IP](../images/wazuh-ip.png)

![Kali IP](../images/kali-ip.png)

![Connectivity Test](../images/ping-test.png)

---

# Attack Surface Discovery – Nmap Analysis

---

## 1. Overview

Attack surface discovery is a critical phase in security assessments, focused on identifying exposed services, open ports, and potential entry points on a target system.

This phase simulates the **reconnaissance stage** of an attack, where adversaries gather information before attempting exploitation.

---

## 2. Objective

The objective of this phase is to:

* Identify open ports and exposed services
* Enumerate running applications on the target system
* Detect potential vulnerabilities associated with these services
* Establish a foundation for subsequent attack simulations

---

## 3. Target Scope

The **Ubuntu server** was selected as the target system, representing a monitored endpoint within the lab environment.

This system is actively sending logs to the SIEM, allowing visibility into attacker activity during scanning.

---

## 4. Attack Methodology

A network scan was conducted using Nmap to simulate reconnaissance behavior typically performed by attackers.

The scan focused on:

* TCP port discovery
* Service enumeration
* Operating system detection

---

## 5. Execution

### Scan Command

```bash
nmap -sS -sV -O -T4 192.168.239.4
```

### Command Breakdown

* `-sS` → TCP SYN (stealth) scan
* `-sV` → Service version detection
* `-O` → Operating system detection
* `-T4` → Aggressive timing for faster scanning

This combination provides a balance between **speed and accuracy** in a controlled lab environment.

---

## 6. Observations

The scan identified multiple open ports and active services on the target system.

These services indicate:

* Accessible network entry points
* Running applications that may be exploitable
* Potential targets for further attack simulation

The presence of SSH (port 22) is particularly significant, as it enables authentication-based attacks such as brute force.

---

## 7. Security Impact

Exposed services increase the overall attack surface of a system.

Risks associated with open ports include:

* Unauthorized access attempts
* Service exploitation due to vulnerabilities
* Weak authentication mechanisms
* Information disclosure

Understanding the attack surface allows defenders to:

* Prioritize monitoring
* Strengthen configurations
* Reduce unnecessary exposure

---

## 8. MITRE ATT&CK Mapping

This activity maps to:

```text
T1046 – Network Service Discovery
```

Attackers use this technique to identify services running on target systems, which can later be exploited or abused.

---

## 9. Key Findings

* The target system exposes multiple network services
* SSH service is accessible and can be targeted for authentication attacks
* Identified services provide a clear path for further attack simulation

These findings directly influenced the next phase, where **SSH brute force attacks** were performed.

---

## 10. Evidence Collection

Screenshots were captured to validate reconnaissance activity and document findings.

> **Note:** Ensure all images are stored within the repository and referenced using relative paths.

---

## 11. Conclusion

This phase successfully identified the attack surface of the target system.

The results provide a clear understanding of exposed services and potential entry points, forming the basis for controlled attack simulation in subsequent phases.

---

## 12. Supporting Evidence

![Nmap Scan Output](../images/nmap-scan.png)

![SSH Service Status](../images/ssh-status.png)

---

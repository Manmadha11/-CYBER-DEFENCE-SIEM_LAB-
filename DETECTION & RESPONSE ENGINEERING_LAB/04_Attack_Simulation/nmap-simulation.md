# Attack Simulation – Nmap Reconnaissance Activity

---

## 1. Overview

This phase simulates active reconnaissance using Nmap to identify how network scanning behavior is generated, logged, and observed within a monitored environment.

Unlike the Attack Surface phase, which focuses on discovery results, this phase emphasizes **attacker activity and detection visibility**.

---

## 2. Objective

The objective of this simulation is to:

* Execute network scanning from an attacker perspective
* Generate reconnaissance-related logs on the target system
* Observe how scanning activity appears in system logs
* Evaluate SIEM visibility for reconnaissance behavior

---

## 3. Target

The **Ubuntu server** was used as the target system.

* Running active services (e.g., SSH)
* Monitored by Wazuh agent
* Capable of generating system and network logs

---

## 4. Attack Methodology

A TCP SYN scan was performed using Nmap to simulate stealth reconnaissance.

This technique is commonly used by attackers to:

* Identify open ports
* Discover running services
* Map potential entry points

---

## 5. Execution

### Scan Command

```bash id="3b4p2k"
nmap -sS -T4 192.168.239.4
```

### Command Breakdown

* `-sS` → SYN (half-open) scan for stealthy probing
* `-T4` → Aggressive timing for faster execution

---

## 6. Observations

During execution:

* The attacker system initiated multiple connection attempts to various ports
* The target system generated logs indicating incoming connection activity
* Network probing behavior was visible in system logs

However, raw logs may not explicitly label the activity as “Nmap scan,” requiring correlation and analysis.

---

## 7. Log Analysis

On the Ubuntu target system:

* Logs were observed using:

  ```bash
  sudo tail -f /var/log/syslog
  ```
* Additional monitoring included:

  ```bash
  sudo tail -f /var/log/auth.log
  ```

Observed indicators:

* Repeated connection attempts from a single source IP
* Sequential or patterned port access
* Short time intervals between requests

These patterns are characteristic of reconnaissance activity.

---

## 8. Security Impact

Network scanning is a precursor to most attacks.

Risks include:

* Exposure of vulnerable services
* Information disclosure about system configuration
* Preparation for targeted exploitation

Early detection of reconnaissance can significantly reduce attack success.

---

## 9. MITRE ATT&CK Mapping

This activity maps to:

```text id="2dqj2o"
T1046 – Network Service Discovery
```

---

## 10. Detection Challenges

During this simulation:

* Raw logs did not clearly indicate “scan activity”
* Detection requires pattern recognition and correlation
* Some scan behaviors may not trigger alerts by default

This highlights the need for **custom detection rules in SIEM systems**.

---

## 11. Detection Relevance

This phase provides insight into:

* How reconnaissance appears in logs
* The limitations of default detection
* The importance of custom rule creation

These observations directly support the **Detection Engineering phase**.

---

## 12. Evidence Collection

Screenshots were captured to validate:

* Nmap scan execution
* Target system logs
* Network activity patterns

> **Note:** Store all images inside the repository and reference them using relative paths.

---

## 13. Conclusion

This phase successfully simulated reconnaissance activity using Nmap and analyzed its visibility within system logs.

The results highlight that:

* Scanning activity is not always explicitly labeled
* Detection requires behavioral analysis
* SIEM customization is necessary for accurate alerting

This phase bridges the gap between **attack execution and detection engineering**.

---

## 14. Supporting Evidence

![Nmap Scan Activity](../GITHUB/nmap-a-scn.png)

![System Log Monitoring](../GITHUB/nmap-scan.png)

![System Log Monitoring](../GITHUB/nmap-scn.png)
---


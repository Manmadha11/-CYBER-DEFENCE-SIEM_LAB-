# Detection Engineering – Custom Command Execution (Reverse Shell) Rule

---

## 1. Overview

This phase focuses on designing a custom detection rule to identify command execution activity, specifically reverse shell behavior.

Execution detection is critical because it represents a **post-exploitation stage**, where an attacker attempts to gain interactive control over a compromised system.

---

## 2. Objective

The objective of this phase is to:

* Detect reverse shell activity using custom logic
* Address misclassification observed in earlier detection phases
* Improve visibility into command execution behavior
* Strengthen post-exploitation monitoring

---

## 3. Detection Gap Identified

During earlier phases:

* Reverse shell activity was detected under **Rule 100102 (Port Scan)**
* The detection system identified network activity but misclassified it
* No dedicated alert for command execution was generated

### Identified Limitation

```text id="gap3"
Reverse shell activity misclassified as reconnaissance (port scanning)
```

---

## 4. Detection Strategy

To address this gap:

* A custom rule is designed to detect **suspicious outbound connections**
* Detection focuses on behavior associated with reverse shells
* Correlation between network activity and command execution is emphasized

---

## 5. Detection Approach

Reverse shell detection is based on:

* Outbound connections to uncommon ports
* Repeated connection attempts to a single external IP
* Execution of shell-related processes (e.g., `/bin/bash`)

---

## 6. Rule Configuration

### File Location (Wazuh Manager)

```bash id="loc3"
/var/ossec/etc/rules/local_rules.xml
```

---

### Custom Rule

```xml id="rule3"
<group name="custom_execution,post_exploitation,">
  <rule id="100103" level="12" frequency="3" timeframe="30">
    <if_group>syslog</if_group>
    <description>Custom Reverse Shell Detection - Suspicious outbound connection</description>
    <mitre>
      <id>T1059</id>
    </mitre>
  </rule>
</group>
```

---

## 7. Rule Explanation

* **Rule ID (100103)** → Custom execution detection rule
* **Level (12)** → High severity (critical activity)
* **Frequency (3)** → Triggers after repeated events
* **Timeframe (30)** → Short detection window
* **if_group (syslog)** → Applies to system/network logs
* **MITRE ID (T1059)** → Command and Scripting Interpreter

---

## 8. Implementation Steps

### Step 1 – Open Rule File

```bash id="cmd7"
sudo nano /var/ossec/etc/rules/local_rules.xml
```

---

### Step 2 – Add Custom Rule

Insert the rule under the appropriate group.

---

### Step 3 – Validate Configuration

```bash id="cmd8"
sudo /var/ossec/bin/wazuh-manager -t
```

---

### Step 4 – Restart Wazuh Manager

```bash id="cmd9"
sudo systemctl restart wazuh-manager
```

---

## 9. Rule Testing

To validate the rule:

* A reverse shell attempt was executed
* Network activity was generated from the target system
* Logs were monitored in the SIEM dashboard

---

## 10. Validation Results

The custom rule triggered alerts indicating:

* Suspicious outbound connections
* Behavior consistent with reverse shell attempts
* High-severity execution-related activity

This confirms improved detection compared to earlier misclassification.

---

## 11. Detection Enhancement Impact

This rule improves detection by:

* Correctly identifying execution-stage attacks
* Reducing misclassification of reverse shell activity
* Providing better visibility into post-exploitation behavior

---

## 12. MITRE ATT&CK Mapping

* **Tactic:** Execution
* **Technique:** Command and Scripting Interpreter (T1059)

This aligns detection with widely recognized threat models.

---

## 13. Detection Considerations

* Reverse shell detection is complex and behavior-based
* Network-only detection may not be sufficient
* Combining process and network monitoring improves accuracy

---

## 14. Detection Insight

```text id="insight1"
Accurate detection requires correlation between multiple data sources, not just network activity.
```

---

## 15. Evidence Collection

Screenshots were captured showing:

* Reverse shell execution attempt
* Wazuh alerts for custom rule 100103
* Supporting system and network logs

> **Note:** Store images using relative paths inside the repository.

---

## 16. Conclusion

This phase demonstrates the ability to identify detection gaps and engineer solutions to improve SIEM accuracy.

The results confirm:

* Successful detection of execution-stage activity
* Improved classification of reverse shell behavior
* Advanced understanding of detection engineering

---

## 17. Supporting Evidence

![CUSTUM RULE](../GITHUB/custum-ruls-pwrshl.png)

![CUSTUM RULE ALERT](../GITHUB/wzh-ssh-brut-id.png)


---

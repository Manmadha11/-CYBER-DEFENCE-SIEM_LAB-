# Detection Engineering – Custom SSH Brute Force Rule

---

## 1. Overview

This phase focuses on designing and implementing a custom detection rule to enhance the identification of SSH brute force attacks.

While default SIEM rules provide baseline detection, custom rule development enables improved visibility, prioritization, and response to high-risk attack patterns.

---

## 2. Objective

The objective of this phase is to:

* Enhance brute force detection using custom logic
* Escalate alert severity for repeated authentication failures
* Improve detection accuracy and response prioritization
* Demonstrate practical detection engineering capability

---

## 3. Detection Gap Identified

During earlier phases:

* Default rule **5716** successfully detected failed SSH login attempts
* However, alerts were generated at moderate severity
* High-frequency attacks required better prioritization

### Identified Limitation

```text id="gap1"
Lack of escalation for repeated authentication failures
```

---

## 4. Detection Strategy

To improve detection:

* A custom rule was created to monitor repeated triggers of rule **5716**
* The rule escalates severity when multiple failures occur in a short time
* This enables faster identification of active brute force attacks

---

## 5. Rule Logic

The custom rule is based on:

* Event frequency (number of failed attempts)
* Time window (attack duration)
* Correlation with existing authentication failure rule

---

## 6. Rule Configuration

### File Location (Wazuh Manager)

```bash id="loc1"
/var/ossec/etc/rules/local_rules.xml
```

---

### Custom Rule

```xml id="rule1"
<group name="custom_bruteforce,authentication,">
  <rule id="100001" level="12" frequency="5" timeframe="60">
    <if_sid>5716</if_sid>
    <description>Custom SSH brute force detection - multiple failures</description>
    <mitre>
      <id>T1110</id>
    </mitre>
  </rule>
</group>
```

---

## 7. Rule Explanation

* **Rule ID (100001)** → Unique identifier for custom detection
* **Level (12)** → High severity (indicates strong attack likelihood)
* **Frequency (5)** → Triggers after 5 failed attempts
* **Timeframe (60)** → Within 60 seconds
* **if_sid (5716)** → Builds on default SSH failure rule
* **MITRE ID (T1110)** → Maps to brute force technique

---

## 8. Implementation Steps

### Step 1 – Open Rule File

```bash id="cmd1"
sudo nano /var/ossec/etc/rules/local_rules.xml
```

---

### Step 2 – Add Custom Rule

Paste the rule inside the file under existing `<group>` or create a new one.

---

### Step 3 – Validate Configuration

```bash id="cmd2"
sudo /var/ossec/bin/wazuh-manager -t
```

---

### Step 4 – Restart Wazuh Manager

```bash id="cmd3"
sudo systemctl restart wazuh-manager
```

---

## 9. Rule Testing

To validate the rule:

* A brute force attack was re-executed using Hydra
* Multiple failed login attempts were generated
* The SIEM dashboard was monitored for alerts

---

## 10. Validation Results

The custom rule successfully triggered:

* High-severity alerts (Level 12)
* Based on repeated authentication failures
* Clearly identifying brute force behavior

This confirms that the rule is functioning as intended.

---

## 11. Detection Enhancement Impact

This custom rule improves detection by:

* Increasing visibility of active attacks
* Reducing noise from low-priority alerts
* Enabling faster incident response
* Highlighting critical threats more effectively

---

## 12. MITRE ATT&CK Mapping

* **Tactic:** Credential Access
* **Technique:** Brute Force (T1110)

This mapping aligns detection with industry-standard threat frameworks.

---

## 13. Evidence Collection

Screenshots were captured showing:

* Custom rule configuration
* Triggered alerts in the Wazuh dashboard
* Correlation with attack activity

> **Note:** Store images in the repository and use relative paths.

---

## 14. Conclusion

This phase demonstrates the successful implementation of a custom detection rule to enhance brute force attack detection.

The results confirm:

* Improved alert prioritization
* Effective use of correlation logic
* Practical detection engineering skills

This establishes a strong foundation for building advanced detection mechanisms.

---

## 15. Supporting Evidence

![CUSTUM RULE](../GITHUB/custum-ruls.png)

![CUSTUM RULE ALERT](../GITHUB/wzh-ssh-brut-id.png)
---

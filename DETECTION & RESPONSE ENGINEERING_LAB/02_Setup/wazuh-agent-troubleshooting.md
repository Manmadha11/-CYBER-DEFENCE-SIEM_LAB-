# Wazuh Agent Troubleshooting Guide

---

## 1. Overview

This document outlines the issues encountered during the Wazuh agent setup and the steps taken to resolve them.

Troubleshooting is a critical component of Security Operations, as real-world environments often present configuration inconsistencies, service failures, and connectivity issues.

This section demonstrates practical debugging skills and operational problem-solving within a SIEM deployment.

---

## 2. Problems Encountered

During the agent setup phase, multiple issues prevented successful communication between the Wazuh agent (Ubuntu) and the Wazuh manager.

### Identified Issues

* Incorrect manager IP configuration
* File permission errors
* Service startup failures
* Agent registration conflicts
* System time synchronization issues

---

## 3. Root Cause Analysis

Each issue was analyzed to determine the underlying cause:

| Issue                      | Root Cause                                 |
| -------------------------- | ------------------------------------------ |
| Agent not connecting       | Incorrect manager IP in configuration file |
| Service not starting       | Stale PID files causing conflicts          |
| Permission denied errors   | Improper file permissions                  |
| Agent registration failure | Existing conflicting agent keys            |
| Authentication issues      | Time mismatch between systems              |

---

## 4. Resolution Steps

The following corrective actions were taken to resolve the issues:

### 4.1 Configuration Fix

* Updated the Wazuh agent configuration file (`ossec.conf`)
* Corrected the manager IP address

---

### 4.2 Permission Correction

* Restored appropriate permissions using `chmod`
* Ensured required files were accessible to Wazuh services

---

### 4.3 Service Conflict Resolution

* Identified and removed stale PID files
* Restarted Wazuh agent services

---

### 4.4 Agent Re-registration

* Deleted existing agent keys from the manager
* Re-registered the agent with a clean configuration

---

### 4.5 Time Synchronization

* Synchronized system time between agent and manager
* Ensured consistent timestamps for authentication and logging

---

## 5. Outcome

After applying the above fixes:

* The Wazuh agent successfully connected to the manager
* Log forwarding resumed normally
* Endpoint monitoring became fully operational

---

## 6. Key Takeaways

* Proper configuration validation is essential before deployment
* Time synchronization is critical for SIEM environments
* Agent registration issues are common in real-world setups
* Systematic troubleshooting helps isolate and resolve issues efficiently

This experience reflects real SOC operational challenges and demonstrates hands-on expertise in managing SIEM infrastructure.

---

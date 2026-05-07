# Common Issues and Fixes – SIEM Lab

---

## 1. Purpose

This document provides a quick reference for common issues encountered during the setup and operation of the SOC lab environment, along with their solutions.

It serves as a troubleshooting guide for maintaining stability during testing and simulation phases.

---

## 2. Common Issues

### 2.1 Agent Not Connecting to Manager

**Possible Causes:**

* Incorrect manager IP address
* Network misconfiguration
* Firewall blocking communication

**Fix:**

* Verify manager IP in `ossec.conf`
* Check network connectivity (ping test)
* Ensure required ports are open

---

### 2.2 Wazuh Manager Service Fails to Start

**Possible Causes:**

* Invalid configuration syntax
* Duplicate rule IDs
* Incorrect rule structure

**Fix:**

* Validate configuration using:

  ```bash
  /var/ossec/bin/wazuh-analysisd -t
  ```
* Correct rule formatting errors
* Ensure unique rule IDs

---

### 2.3 No Logs Appearing in Dashboard

**Possible Causes:**

* Agent not forwarding logs
* Incorrect log file configuration
* Log collector not enabled

**Fix:**

* Verify `<localfile>` configuration
* Check agent service status
* Restart Wazuh services

---

### 2.4 Active Response Not Triggering

**Possible Causes:**

* Incorrect rule ID mapping
* Misconfigured active response block
* Script execution failure

**Fix:**

* Ensure correct `rules_id` is used
* Verify command configuration in `ossec.conf`
* Check script permissions and logs

---

### 2.5 Network Connectivity Issues

**Possible Causes:**

* Different network adapters (NAT vs Host-Only)
* Incorrect subnet configuration

**Fix:**

* Ensure all VMs use the same network (Host-Only)
* Verify IP addresses are in the same subnet

---

## 3. Conclusion

Maintaining a stable SIEM environment requires continuous validation and troubleshooting.

This guide provides a quick reference to resolve common issues efficiently and ensure smooth operation of the lab during attack simulation and detection phases.

---

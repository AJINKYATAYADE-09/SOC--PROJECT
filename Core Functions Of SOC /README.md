# 🛡️ Core Functions of a Security Operations Center (SOC)

Welcome to this repository dedicated to understanding the **core functions** of a **Security Operations Center (SOC)** — the beating heart of an organization's cybersecurity defense.

This guide reflects my personal exploration and hands-on learning in cybersecurity operations, designed to be a helpful resource for beginners, practitioners, and anyone curious about how a SOC works.

---

## 🚨 What is a SOC?

A **Security Operations Center (SOC)** is a centralized unit that deals with security issues on an organizational and technical level. It consists of a team of cybersecurity professionals responsible for monitoring, detecting, analyzing, and responding to security incidents.

---

## 🧠 Core Functions of a SOC

Below are the **five core functions** of an effective SOC:

---

1. 🔍 **Security Monitoring**

   - **Continuous monitoring** of networks, systems, endpoints, and applications.
   - Detects unusual or malicious behavior using tools like SIEM, IDS/IPS, EDR, etc.
   - Provides **real-time visibility** into threats.

   > Tools Used: Splunk, ELK Stack, QRadar, Suricata, Zeek

---

2. 🧪 **Incident Detection**

   - Analyzes log data and telemetry to **identify potential security incidents**.
   - Uses techniques such as correlation rules, threat intelligence, and anomaly detection.
   - Focuses on **minimizing detection time (MTTD)**.

   > Includes: Alert triaging, use-case development, threat hunting

---

3. 🚑 **Incident Response**

   - Takes immediate actions when a threat is confirmed:
     - Containment
     - Eradication
     - Recovery
   - Coordinates with other teams to **remediate attacks** and prevent escalation.
   - Maintains documentation and post-incident analysis.

   > Frameworks: NIST IR Lifecycle, MITRE ATT&CK

---

4. 📊 **Log Collection and Management**

   - Collects logs from various sources: firewalls, servers, endpoints, cloud, apps.
   - Ensures logs are normalized, time-synced, and securely stored.
   - Critical for **forensics, compliance, and threat detection**.

   > Forwarders and Aggregators: Syslog, Splunk Universal Forwarder, Beats (Filebeat, Winlogbeat)

---

5. 📚 **Threat Intelligence and Reporting**

   - Integrates **Threat Intelligence Feeds (TI)** to enhance detection capabilities.
   - Generates **dashboards and reports** for technical and executive audiences.
   - Tracks **KPIs like MTTD, MTTR, alert volume, false positives**.

   > Examples: STIX/TAXII, MISP, OpenCTI, Threat Intelligence Platforms

---

🧭 **SOC Operations Lifecycle**  
[Monitoring] ➜ [Detection] ➜ [Analysis] ➜ [Response] ➜ [Recovery] ➜ [Reporting]

---

# 📊 Splunk Enterprise and Forwarders Lab Setup

This directory contains all documentation and resources for setting up Splunk Enterprise with Universal Forwarder on Ubuntu (VMware), enabling centralized log collection and real-time security monitoring.

---

## 📄 Included Files

- **SPLUNK-SETUP-AJINKYATAYADE-09.pdf**  
  Complete lab walkthrough for setting up Splunk Enterprise and Universal Forwarder.

---

## 🧰 Tools & Technologies Used

- **Splunk Enterprise** (Windows Server - Central SIEM)
- **Splunk Universal Forwarder** (Ubuntu Client in VMware)
- **Ubuntu Server**
- **PuTTY** (SSH client)
- **UFW Firewall** (port management)

---

## 🛠️ Overview

- **Log Collection:** Ubuntu forwards logs to Splunk Enterprise over port 9997.
- **Monitoring:** Real-time analysis using Splunk dashboards.
- **SOC Training:** Practice event correlation, search, and alerting skills.

---

## 🚀 Quick Steps

1. **Install Splunk Enterprise** on Windows  
   [Download](https://www.splunk.com/en_us/download/splunk-enterprise.html) and follow installer instructions.

2. **Set up Ubuntu Server in VMware**  
   Use PuTTY to SSH into Ubuntu.

3. **Install Universal Forwarder**  
   ```bash
   sudo ufw allow 22/tcp
   sudo ufw allow 9997/tcp
   wget https://download.splunk.com/products/universalforwarder/releases/9.4.3/linux/splunkforwarder-9.4.3-linux-amd64.deb
   sudo dpkg -i splunkforwarder-9.4.3-linux-amd64.deb
   cd /opt/splunkforwarder/bin
   sudo ./splunk start --accept-license
   sudo ./splunk enable boot-start
   sudo ./splunk add forward-server <SPLUNK_SERVER_IP>:9997 -auth admin:admin
   sudo ./splunk add monitor /var/log/auth.log -auth admin:admin
   sudo ./splunk restart
   ```

4. **Enable Receiving on Splunk Enterprise**  
   Settings → Forwarding and Receiving → Configure Receiving → Add port 9997.

---

## ✅ Expected Output

- Ubuntu `/var/log/auth.log` entries visible in Splunk Enterprise.
- Analyze logs in Search & Reporting → Data Summary → Hosts.

---

## 👤 Author

**AJINKYA TAYADE**  
📧 Ajinkyatayade43@gmail.com

---

For the full step-by-step guide, refer to **SPLUNK-SETUP-AJINKYATAYADE-09.pdf** in this folder.

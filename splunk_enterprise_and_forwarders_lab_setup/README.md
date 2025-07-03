# 📊 Splunk Enterprise and Forwarders Lab Setup

This directory contains all documentation and resources for setting up Splunk Enterprise with Universal Forwarder on Ubuntu (VMware), enabling centralized log collection and real-time security monitoring.

---

## 📄 Included Files

- **Splunk-Setup-.pdf**  
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

**Ajinkya Tayade**  
📧 Ajinkyatayade43

---

For the full step-by-step guide, refer to **Splunk-Setup-.pdf** in this folder.

# 🚨 Wazuh High-Severity Alert Email Automation (n8n Integration)

## 📌 Overview
This project implements automated SOC alerting by integrating **Wazuh SIEM with n8n workflow automation** to send real-time email notifications for high-severity security events.

The system detects critical alerts in Wazuh and automatically triggers an n8n workflow that processes the alert data and sends structured email notifications to analysts for rapid response.


## 🎯 Objectives
- Automate alert notification for critical threats
- Reduce manual SOC monitoring effort
- Improve incident response time
- Demonstrate real-world SIEM + SOAR integration


## 🏗️ Architecture
Wazuh Agent → Wazuh Manager → n8n Webhook → Email Notification


## ⚙️ Key Features
- High-severity alert detection
- Automated workflow triggering
- Real-time email notification
- Centralized monitoring support
- SOC-ready alert pipeline


## 🧩 Technologies Used
- Wazuh SIEM
- n8n Automation
- Linux (Ubuntu)
- Webhooks
- Email SMTP Integration


## 🔍 Workflow Logic
1. Wazuh detects a high-severity alert
2. Alert is forwarded to n8n via webhook
3. n8n processes alert data
4. Email notification is generated
5. SOC analyst receives alert instantly


## 📊 Use Case
This setup simulates a real SOC environment where critical security events must be reported immediately without manual intervention.


## 🧠 Skills Demonstrated
- SIEM Integration
- Security Automation (SOAR concepts)
- Webhook Configuration
- Incident Response Workflow Design
- Log Monitoring & Alert Engineering
- Email Alert Automation



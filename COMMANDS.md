# 🧾 Wazuh → n8n Alert Automation
## Commands & Configuration Guide

This document contains all technical commands and configuration steps used to implement High-Severity Alert Email Automation using Wazuh SIEM and n8n.


# 1️⃣ Wazuh Configuration

## 📂 Edit Wazuh Main Configuration File

```bash
sudo nano /var/ossec/etc/ossec.conf
```

## 🔗 Add Webhook Integration Block

Add this inside `<ossec_config>`:

```xml
<integration>
  <name>custom-webhook</name>
  <hook_url>http://<n8n-server>:5678/webhook/wazuh-alert</hook_url>
  <level>12</level>
  <alert_format>json</alert_format>
</integration>
```

## 🔄 Restart Wazuh Manager

```bash
sudo systemctl restart wazuh-manager
```

## 📊 Verify Wazuh Status

```bash
sudo systemctl status wazuh-manager
```

## 📄 Monitor Alerts

```bash
sudo tail -f /var/ossec/logs/alerts/alerts.json
```

## 📜 Check Wazuh Logs

```bash
sudo tail -f /var/ossec/logs/ossec.log
```


# 2️⃣ n8n Installation & Setup

## 📦 Install Node.js and npm

```bash
sudo apt install nodejs npm -y
```

## 📦 Install n8n Globally

```bash
npm install n8n -g
```

## ▶️ Start n8n

```bash
n8n start
```

## 🌐 Access n8n Dashboard

Open in browser:

http://localhost:5678

## 🔍 Verify n8n Process

```bash
ps aux | grep n8n
```


# 3️⃣ n8n Workflow Configuration

## 🔔 Create Webhook Node

- Method: POST  
- Copy Production Webhook URL  
- Paste URL inside Wazuh `<hook_url>`  

## 📧 Configure Email Node (SMTP)

Map alert fields such as:

```
{{$json["rule"]["description"]}}
{{$json["agent"]["name"]}}
{{$json["rule"]["level"]}}
```

Activate workflow after configuration.


# 4️⃣ Testing & Validation

## 🧪 Trigger High-Severity Alert

Example (SSH brute force simulation):

```bash
sudo hydra -l root -P /usr/share/wordlists/rockyou.txt <target-ip> ssh
```

## 📊 Confirm Alert Reception

```bash
sudo tail -f /var/ossec/logs/alerts/alerts.json
```

## 📧 Confirm Email Delivery

Check inbox for high-severity notification.


# 5️⃣ Troubleshooting

## 🔍 Check Wazuh Logs

```bash
sudo journalctl -u wazuh-manager
```

## 🔄 Restart Services

```bash
sudo systemctl restart wazuh-manager
pkill n8n
n8n start
```

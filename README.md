### AIM – Active IDS Monitoring


### A Security Enchancement Layer for IDS Resilience

---

### 🛡️ Project Overview

This project, **Active IDS Monitoring (AIM)**, introduces a robust, multi-layered cybersecurity defense system designed to protect a critical Intrusion Detection System (IDS) from both internal and external threats. The core of AIM is a "defense-in-depth" strategy: Snort, a Network-Based IDS (NIDS), is deployed to protect the network's perimeter, while Wazuh, a Host-Based IDS (HIDS), acts as a dedicated security layer to protect the Snort installation itself.

By combining these two powerful open-source tools, AIM ensures that your primary IDS is always operational and untampered. If an attacker or malicious insider attempts to disable Snort, modify its rules, or delete its logs, Wazuh will immediately detect the change and alert the security team in real-time.

---

### ✨ Key Features

* **Snort NIDS Deployment:** A fully functional Snort IDS is installed and configured on a Windows VM to actively monitor and log suspicious network traffic, including port scans and DoS attempts.
* **Wazuh HIDS Integration:** Wazuh is set up on a separate Ubuntu VM to continuously monitor the integrity of Snort's configuration files, rules, and logs. It serves as a security-enhancing layer that adds a crucial second line of defense.
* **Real-Time File Integrity Monitoring (FIM):** The Wazuh Syscheck module is configured to actively track and report any unauthorized changes or deletions within the Snort directory, ensuring that your IDS rules and logs are never compromised.
* **Snort Service Monitoring:** The system monitors the Snort service status, automatically generating an alert if the service is stopped or restarted without authorization. This feature is critical for preventing an attacker from simply "turning off" your primary line of defense.
* **Automated Alerting:** Alerts for file tampering and service disruption are generated in real-time and are integrated with Telegram and email for instant notifications.
* **Threat Simulation and Validation:** The system was rigorously tested with simulated scenarios, such as an admin stopping the Snort service or deleting rule files, to validate the effectiveness of the monitoring and alerting mechanisms.

---

### ⚙️ Technologies Used

* **Snort:** An open-source NIDS that uses a rule-based engine to perform real-time traffic analysis.
* **Wazuh (v4.12.0):** An open-source HIDS and Security Information and Event Management (SIEM) platform used for host monitoring, file integrity, and centralized alerting.
* **Telegram:** A messaging platform used for real-time alert notifications to the security team.
* **Gmail:** A popular email service used to send alerts and notifications.
* **VMware Workstation:** A virtualization platform used to create a secure, isolated lab environment for development and testing.
* **Windows & Ubuntu:** The operating systems used for the Snort and Wazuh installations, respectively.

---

### 🚀 How to Set Up

1.  **Deploy VMs:** Create two VMs using VMware, one with Windows 10 for Snort and one with Ubuntu 22.04 for the Wazuh manager.
2.  **Snort Setup:** Install Snort on the Windows VM, configure it to run as a service, and verify its ability to detect basic threats.
3.  **Wazuh Installation:** Follow the official [Wazuh installation guide](https://documentation.wazuh.com/) to set up the Wazuh manager on the Ubuntu VM.
4.  **Agent Configuration:** Install the Wazuh agent on the Windows VM and configure `ossec.conf` to monitor the Snort directory.
5.  **Custom Rules:** Add the custom rules provided in the `configs/` folder to your Wazuh manager to enable service monitoring and specific alerts.
6.  **Email (Gmail) Integration:** Configure Wazuh to send email alerts. This requires adding your Gmail SMTP details to the `/var/ossec/etc/ossec.conf` file on the Wazuh manager. Make sure to use an App Password for your Gmail account for security.
7.  **Telegram Integration:** Set up a Telegram bot via [@BotFather](https://t.me/botfather) and configure the `telegram_alert.py` script to forward Wazuh alerts to your security channel.

---

### 🎓 Authors

* **S. Yathurshan**
* **M. S. H. Azeel**
* **Thenupa Methnuka**
* **Ravishka Lashan**
* **Kasun Thilanga**
* **Sethnim Dilneth**


#  📌 Overview

This project simulates a Security Operations Centre (SOC) environment by leveraging Splunk Enterprise to collect, analyze, and visualize Windows Event Logs. Focused on detecting security threats like failed login attempts, brute-force attacks, and user-based anomalies, this project provides hands-on experience with SIEM (Security Information and Event Management) tools, making it ideal for cybersecurity professionals and enthusiasts.



# 🎯 Objectives
- Collect and Centralize Logs: Aggregate Windows Event Logs (Security and System) using Splunk Universal Forwarder.

- Detect Threats: Identify suspicious activities such as brute-force attacks and account enumeration.

- Visualize Data: Create interactive dashboards for real-time monitoring and analysis.

- Develop SIEM Skills: Gain practical experience with Splunk queries and SOC workflows.


# 🛠️ Tools Used
## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **VMware Fusion / UTM** | Host virtualization (to run Windows 11 VM) |
| **Windows 11 VM** | Generates logs and runs Splunk Universal Forwarder |
| **Splunk Enterprise** | SIEM for log indexing, analysis, and dashboards |
| **Splunk Universal Forwarder** | Lightweight agent to forward Windows logs to Splunk |
| **Windows Event Logs** | Source of security events (e.g., Event ID 4625) |


# 📂 Project Structure

## Data Collection

- **Splunk Enterprise** installed on macOS (localhost) with port `9997` enabled for log ingestion.
- **Splunk Universal Forwarder** configured on Windows 11 VM to monitor:
  - `WinEventLog://Security`
  - `WinEventLog://System`
- Created a dedicated Splunk index: `wineventlog`.

## Attack Simulation

- Triggered multiple failed logins using fake accounts (e.g., `admin`, `John`, `Randy`) to generate Event ID `4625`.

## Detection Use Cases

- **Brute-force Attacks**: Detected repeated failed logins across accounts.
- **Account Enumeration**: Identified login attempts with non-existent usernames.
- **Login Failure Trends**: Tracked spikes in authentication failures over time.

## SPL Queries

Example queries for analyzing log data:

```spl
index=wineventlog EventCode=4625  
| stats count by Account_Name, host  
| sort -count  
```
```spl
index=wineventlog EventCode=4625  
| timechart span=1m count by Account_Name  
```
# 📊 Key Outcomes

- Successfully centralized and analyzed Windows Event Logs in Splunk.

- Detected simulated attacks using custom SPL queries.

- Built actionable dashboards for SOC monitoring.

- Developed foundational SIEM skills applicable to real-world cybersecurity roles.
# 🚀 How to Use This Project

1. **Set Up Splunk Enterprise:** Install and configure Splunk on your   local machine or server.

2. **Deploy Universal Forwarder:** Install the forwarder on Windows VM and point it to your Splunk instance.

3. **Simulate Attacks:** Use the Windows login screen to generate failed login events.

4. **Run SPL Queries:** Use the provided queries to analyze logs and detect anomalies.

5. **Create Dashboards:** Visualize the data for real-time monitoring.
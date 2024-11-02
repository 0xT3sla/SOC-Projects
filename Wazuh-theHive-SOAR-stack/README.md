# SOC Automation Project with Wazuh, theHive

This project aims to develop a fully automated Security Operations Center (SOC) solution from scratch, integrating Wazuh for monitoring and TheHive for case management. By leveraging the capabilities of SOAR (Security Orchestration, Automation, and Response), the project explores creative ways to automate threat detection, response, and case management workflows within a SOC environment.

- **Tools**: Wazuh (SIEM/Endpoint Security) and TheHive (Case Management)
- **Scope**: Full implementation from zero to a highly automated SOC solution
- **Goal**: Build a robust, automated SOC environment, pushing the limits of security automation

---

## SOC Automation Project Setup

### Overview
This document outlines the initial setup for the SOC Automation Project, where we establish a foundational SOC environment using tools like Sysmon, Wazuh, and TheHive. This setup phase prepares essential systems and services for monitoring, case management, and incident response capabilities in later stages.

### Project Goal
Set up core components to build a fully automated SOC environment with Wazuh and TheHive for monitoring and incident management.

### Setup Structure

#### Step 1: Installing and Configuring Windows 10 with Sysmon
- **Objective**: Install Windows 10 and set up Sysmon to monitor system activities for enhanced threat detection.
- **Actions**:
  - Install Windows 10 on a virtual machine.
  - Set up Sysmon to log detailed system events for activity tracking.

#### Step 2: Setting Up Wazuh as the SIEM Platform
- **Objective**: Install Wazuh, an open-source SIEM tool, to provide security analytics and enhance incident response.
- **Actions**:
  - Download and install Wazuh on a virtual machine.
  - Configure Wazuh for initial threat detection and monitoring.

![alt text](./images/wazuh-dashboard.png)
#### Step 3: Configuring a Secure Firewall for Virtual Machines
- **Objective**: Secure virtual machines from unauthorized access by setting up a robust firewall.
- **Actions**:
  - Set firewall rules to control and restrict access to the virtual machines.

![alt text](./images/firewall-do.png)

#### Step 4: Installing TheHive for Incident Response Management
- **Objective**: Set up TheHive for efficient case management, allowing for systematic incident tracking and response.
- **Actions**:
  - Install TheHive on a virtual machine.
  - Configure TheHive to handle incident reports and case assignments.

### Key Insights

- 🔍 **Sysmon on Windows 10**: Provides real-time monitoring of system activities, enabling security event analysis.
- 🌐 **Wazuh as an Open-Source SIEM**: Offers essential tools for incident response and security analytics.
- 🔐 **Firewall Configuration**: Adds a layer of security to protect against unauthorized access, emphasizing the need for secure configurations.
- 📊 **Incident Response with TheHive**: Facilitates organized case management, crucial for effective SOC operations.
- 📋 **Software Integrity Verification**: Checking SHA256 checksums ensures the integrity of downloaded software, reducing the risk of tampered files.

---

## Installation of Wazuh
![alt text](./images/wazuh-logo.png)
### Step 1: Install Wazuh 4.7
Run the following command to download and execute the Wazuh installation script:
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
### Step 2: Extract Wazuh Credentials
After installation, extract the Wazuh credentials using the following command:

```bash
sudo tar -xvf wazuh-install-files.tar
```

---


# Installation of TheHive
![alt text](./images/theHive-logo.png)
## Overview
TheHive is an open-source incident response platform that enables security teams to efficiently manage and respond to security incidents. This guide provides the steps necessary to install TheHive on your system.

## Prerequisites
Ensure that your system meets the following requirements:
- A compatible Linux distribution.
- Sufficient privileges to execute commands as a superuser (sudo).
- A working internet connection to download the necessary packages.

### Step 1: Add TheHive Repository Key
First, download and add the GPG key for TheHive to ensure the authenticity of the packages:

```bash
wget -O- https://archives.strangebee.com/keys/strangebee.gpg | sudo gpg --dearmor -o /usr/share/keyrings/strangebee-archive-keyring.gpg
```
### Step 2: Add TheHive Repository
Next, add TheHive's repository to your system's sources list:

```bash
echo 'deb [signed-by=/usr/share/keyrings/strangebee-archive-keyring.gpg] https://deb.strangebee.com thehive-5.2 main' | sudo tee -a /etc/apt/sources.list.d/strangebee.list
```
### Step 3: Update Package List
Update your package list to include the newly added TheHive repository:

```bash
sudo apt-get update
```
---
## Wazuh Agent Installation on Windows via PowerShell Command

#### 1. Generate the PowerShell Command from Wazuh Dashboard

1. **Log in to the Wazuh Dashboard**: Open your web browser and log into your Wazuh dashboard.
2. **Navigate to the Agents Section**:
   - In the dashboard, go to **"Agents"** in the left-hand menu.
3. **Add New Agent**:
   - Click on **"Add agent"** to generate an installation command for your Windows machine.
4. **Enter the Wazuh Server's Public Address**:
   - When prompted, provide the public IP address or domain name of your Wazuh server. This allows the agent to communicate with the correct manager.
5. **Copy the PowerShell Command**:
   - After entering the server address, a PowerShell command will be generated for the Windows agent. Copy this command for use in the next step.

#### 2. Run the PowerShell Command on the Windows Machine

1. **Open PowerShell as Administrator**:
   - On the Windows machine, open **PowerShell** with administrator privileges.
2. **Paste and Run the Command**:
   - Paste the copied PowerShell command into the PowerShell window and press **Enter**.
   - This command will download, install, and configure the Wazuh agent to communicate with the Wazuh manager.

#### 3. Verify the Agent Status in Wazuh Dashboard

1. Return to the Wazuh dashboard and navigate to **"Agents"**.
2. Confirm that the Windows agent appears in the list and shows as **active**.

    ![alt text](./images/agent-added.png)

Your Windows agent is now installed and reporting to the Wazuh manager! This method allows you to set up the agent in one step without manually downloading or configuring the installer.

---

# Basic SOC / SIEM Security Monitoring Lab

## Project Overview

This project documents a basic Security Operations Center (SOC) and SIEM security monitoring lab using Windows Event Viewer, Wazuh SIEM, Sysmon, Windows Firewall logs, Microsoft Defender, Kali Linux, Nmap, and Wireshark.

The lab started with local Windows security log monitoring using Event Viewer, then expanded into centralized log monitoring using Wazuh SIEM. Additional phases included Sysmon monitoring, Active Directory security events, firewall/network testing, endpoint security review, and packet capture analysis using Wireshark.

This lab is designed to build foundational blue-team cybersecurity skills for entry-level IT support, cybersecurity, and SOC analyst roles.

---

## Objectives

- Build a basic SOC/security monitoring lab environment
- Review Windows Security logs using Event Viewer
- Identify failed and successful logon events
- Monitor Active Directory account activity
- Deploy Wazuh SIEM on Ubuntu Server
- Add Windows endpoints as Wazuh agents
- Detect Windows security events through Wazuh Threat Hunting
- Monitor Sysmon endpoint activity
- Review Windows Firewall and Filtering Platform events
- Test network traffic using Kali Linux and Nmap
- Capture and analyze traffic using Wireshark
- Document security findings and incident response results

---

## Lab Environment

| Device | Role | Operating System | IP Address | Purpose |
|---|---|---|---|---|
| Wazuh-Server | SIEM Server | Ubuntu Server 24.04 LTS | 192.168.10.50 | Collects and analyzes security logs |
| Server2022 | Domain Controller / Wazuh Agent / Web Server | Windows Server 2022 | 192.168.10.10 | Generates domain, account, firewall, and web traffic events |
| Desktop1 | Windows Endpoint / Wazuh Agent | Windows 10 Pro | 192.168.10.x | Generates Windows endpoint and logon events |
| Kali-Linux | Testing Machine | Kali Linux | 192.168.10.30 | Used for ping, Nmap, and Wireshark traffic analysis |

---

## Tools Used

- Wazuh SIEM
- Ubuntu Server 24.04 LTS
- Windows Server 2022
- Windows 10 Pro
- Windows Event Viewer
- Windows Security Logs
- Active Directory Users and Computers
- Sysmon
- Windows Firewall Logging
- Microsoft Defender
- PowerShell
- Command Prompt
- Kali Linux
- Nmap
- Wireshark
- XAMPP / Apache
- VirtualBox

---

## Key Security Events

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4722 | User account enabled |
| 4724 | Password reset attempted |
| 4725 | User account disabled |
| 4728 | User added to security-enabled global group |
| 4740 | User account locked out |
| 4767 | User account unlocked |
| 1102 | Windows Security log cleared |
| 5156 | Windows Filtering Platform allowed connection |

---

## Phase 1: Windows Event Viewer Monitoring

In the first phase, Windows Event Viewer was used to manually review local and domain security logs.

### Activities Completed

- Reviewed Windows Security logs
- Detected failed logon event using Event ID 4625
- Detected successful logon event using Event ID 4624
- Detected user account creation using Event ID 4720
- Detected account lockout using Event ID 4740
- Verified account unlock through Active Directory Users and Computers

### Event Viewer Evidence

#### Event Viewer Security Log
![Event Viewer Security Log](screenshots/01-event-viewer-security-log.png)

#### Failed Logon Event - 4625
![Failed Logon Event 4625](screenshots/02-failed-logon-event-4625.png)

#### Successful Logon Event - 4624
![Successful Logon Event 4624](screenshots/03-successful-logon-event-4624.png)

#### User Account Created Event - 4720
![User Created Event 4720](screenshots/04-user-created-event-4720.png)

#### Account Locked Out Message
![Account Locked Out Message](screenshots/05-account-locked-out-login-message.png)

#### Account Lockout Event - 4740
![Account Lockout Event 4740](screenshots/06-account-lockout-event-4740.png)

#### Account Unlock Verification
![Account Unlock Verification](screenshots/07-unlock-account-aduc.png)

---

## Phase 2: Wazuh SIEM Monitoring

In the second phase, Wazuh SIEM was deployed on Ubuntu Server to collect and monitor Windows security logs from domain endpoints.

### Activities Completed

- Installed and configured Wazuh Server on Ubuntu Server
- Accessed the Wazuh web dashboard
- Added Windows 10 Desktop1 as a Wazuh agent
- Added Windows Server 2022 Domain Controller as a Wazuh agent
- Verified active Wazuh agents
- Detected failed logon events using Event ID 4625
- Detected user account creation using Event ID 4720
- Detected account lockout using Event ID 4740
- Detected account unlock using Event ID 4767
- Reviewed alerts through Wazuh Threat Hunting

### Wazuh Evidence

#### Wazuh Dashboard
![Wazuh Dashboard](screenshots/09-wazuh-dashboard.png)

#### Desktop1 Wazuh Agent Active
![Desktop1 Wazuh Agent Active](screenshots/11-wazuh-agent-desktop1-active.png)

#### Desktop1 Events in Wazuh
![Desktop1 Wazuh Events](screenshots/12-wazuh-desktop1-events.png)

#### Server2022 Wazuh Agent Active
![Server2022 Wazuh Agent Active](screenshots/13-wazuh-agent-server2022-active.png)

#### Failed Logon Event - 4625
![Wazuh Failed Logon 4625](screenshots/14-wazuh-failed-logon-4625-server2022.png)

#### Failed Logon Event Filtered - 4625
![Wazuh Failed Logon 4625 Filtered](screenshots/15-wazuh-failed-logon-4625-filtered.png)

#### User Account Created - 4720
![Wazuh User Created 4720](screenshots/16-wazuh-user-created-4720.png)

#### Account Lockout - 4740
![Wazuh Account Lockout 4740](screenshots/17-wazuh-account-lockout-4740.png)

#### Account Unlock - 4767
![Wazuh Account Unlock 4767](screenshots/18-wazuh-account-unlocked-4767.png)

---

## Phase 3: Sysmon Monitoring with Wazuh

In this phase, Sysmon was used to collect more detailed Windows endpoint activity. Sysmon logs were reviewed locally through Event Viewer and then monitored centrally in Wazuh.

### Activities Completed

- Enabled Sysmon Operational logs on Desktop1
- Verified Sysmon logs in Windows Event Viewer
- Confirmed Sysmon events were collected by Wazuh
- Reviewed Sysmon Process Create events in Wazuh Threat Hunting
- Applied custom Wazuh detection rule for improved monitoring

### Sysmon Evidence

#### Sysmon Operational Log on Desktop1
![Sysmon Operational Log Desktop1](screenshots/19-sysmon-operational-log-desktop1.png)

#### Sysmon Events in Wazuh
![Wazuh Sysmon Events Desktop1](screenshots/20-wazuh-sysmon-events-desktop1.png)

#### Sysmon Process Create Event
![Wazuh Sysmon Process Create Event](screenshots/21-wazuh-sysmon-process-create-event1.png)

#### Wazuh Manager After Custom Rule
![Wazuh Manager After Custom Rule](screenshots/24-wazuh-manager-after-custom-rule.png)

---

## Phase 4: Active Directory Security Monitoring

In this phase, additional Active Directory account security events were generated and monitored through both Windows Event Viewer and Wazuh.

### Activities Completed

- Detected password reset event
- Detected disabled user account event
- Detected enabled user account event
- Detected user added to security group event
- Detected cleared Windows Security log event
- Verified events in both Event Viewer and Wazuh

### Active Directory Monitoring Evidence

#### Password Reset Event - 4724
![Event Viewer Password Reset 4724](screenshots/26-event-viewer-password-reset-4724.png)

#### User Disabled Event - 4725
![Event Viewer User Disabled 4725](screenshots/28-event-viewer-user-disabled-4725.png)

#### User Disabled Event in Wazuh - 4725
![Wazuh User Disabled 4725](screenshots/29-wazuh-user-disabled-4725.png)

#### User Enabled Event - 4722
![Event Viewer User Enabled 4722](screenshots/30-event-viewer-user-enabled-4722.png)

#### User Enabled Event in Wazuh - 4722
![Wazuh User Enabled 4722](screenshots/31-wazuh-user-enabled-4722.png)

#### User Added to Group Event - 4728
![Event Viewer User Added to Group 4728](screenshots/32-event-viewer-user-added-group-4728.png)

#### User Added to Group Event in Wazuh - 4728
![Wazuh User Added to Group 4728](screenshots/33-wazuh-user-added-group-4728.png)

#### Security Log Cleared Event - 1102
![Event Viewer Security Log Cleared 1102](screenshots/34-event-viewer-security-log-cleared-1102.png)

#### Security Log Cleared Event in Wazuh - 1102
![Wazuh Security Log Cleared 1102](screenshots/35-wazuh-security-log-cleared-1102.png)

---

## Phase 5: Windows Firewall and Network Traffic Monitoring

In this phase, Windows Firewall logging and audit policies were enabled on Server2022. Kali Linux was used as a testing machine to generate network traffic toward the Windows Server.

### Activities Completed

- Enabled Windows Firewall logging on Server2022
- Enabled Filtering Platform audit policy
- Configured Kali Linux with a static IP address
- Verified connectivity from Kali to Server2022
- Performed Nmap scan from Kali to Server2022
- Reviewed Windows Filtering Platform events
- Created a firewall rule to block Kali traffic to port 80
- Verified blocked port result using Nmap

### Firewall and Network Testing Evidence

#### Windows Firewall Logging Enabled
![Server2022 Firewall Logging Enabled](screenshots/36-server2022-firewall-logging-enabled.png)

#### Filtering Platform Audit Enabled
![Server2022 Filtering Platform Audit Enabled](screenshots/37-server2022-filtering-platform-audit-enabled.png)

#### Kali Static IP Configuration
![Kali Static IP 192.168.10.30](screenshots/38-kali-static-ip-192-168-10-30.png)

#### Kali Ping to Server2022 Successful
![Kali Ping Server2022 Success](screenshots/39-kali-ping-server2022-success.png)

#### Kali Nmap Scan to Server2022
![Kali Nmap Scan Server2022](screenshots/40-kali-nmap-scan-server2022.png)

#### Filtering Platform Event Details - 5156
![Event Viewer Filtering Platform Event Details 5156](screenshots/42-event-viewer-filtering-platform-event-details-5156.png)

#### Filtering Platform Events - 5156
![Event Viewer Filtering Platform Events 5156](screenshots/42-event-viewer-filtering-platform-events-5156.png)

#### Firewall Rule Blocking Kali Port 80
![Server2022 Block Kali Port 80 Rule](screenshots/44-server2022-block-kali-port80-rule.png)

#### Nmap Scan Showing Blocked Port 80
![Kali Nmap Blocked Port 80](screenshots/45-kali-nmap-blocked-port80.png)

---

## Phase 6: Microsoft Defender and PowerShell Recon Testing

In this phase, Windows Security and Microsoft Defender were reviewed as part of endpoint security monitoring. A PowerShell recon test was also performed to generate endpoint activity for monitoring practice.

### Activities Completed

- Verified Windows Security / Microsoft Defender status
- Reviewed Defender Protection History
- Tested PowerShell-based reconnaissance commands on Desktop1
- Documented endpoint activity for security monitoring practice

### Defender and PowerShell Evidence

#### Windows Security Defender Enabled
![Windows Security Defender Enabled](screenshots/48-windows-security-defender-enabled.png)

#### Defender Protection History - EICAR Test
![Defender Protection History EICAR](screenshots/49-defender-protection-history-eicar.png)

#### Desktop1 PowerShell Recon Commands
![Desktop1 PowerShell Recon Commands](screenshots/52-desktop1-powershell-recon-commands.png)

---

## Phase 7: Wireshark Network Traffic Analysis

In this phase, Wireshark was used on Kali Linux to capture and analyze network traffic between Kali and Server2022. The test focused on HTTP traffic to the XAMPP web server hosted on Server2022.

### Activities Completed

- Opened the Server2022 XAMPP web page from Kali
- Captured traffic between Kali and Server2022
- Applied Wireshark display filters
- Identified TCP handshake traffic
- Identified HTTP GET request and HTTP response
- Documented packet-level network activity

### Wireshark Evidence

#### Captured Traffic Between Kali and Server2022
![Wireshark Captured Server2022 Traffic](screenshots/55-wireshark-captured-server2022-traffic.png)

#### TCP Handshake to Server2022
![Wireshark TCP Handshake Server2022](screenshots/56-wireshark-tcp-handshake-server2022.png)

#### HTTP Packet Details
![Wireshark HTTP Packet Details](screenshots/57-wireshark-http-packet-details.png)

---
## OpenVPN Remote Access VPN

![OpenVPN client connected](screenshots/openvpn-client-connected-status.png)

OpenVPN Remote Access VPN successfully established — pfSense Status > OpenVPN 
shows an active client session for "vpnuser" with a tunnel IP of 10.10.99.2, 
confirming a working site-to-client VPN connection into the internal LAN 
(192.168.10.0/24).


## Incident Response Notes

During the lab, several security-related activities were generated and reviewed. These included failed logons, successful logons, user creation, account lockout, account unlock, password reset, user disable/enable activity, group membership changes, cleared security logs, firewall/network activity, and HTTP traffic capture.

The purpose of the investigation was to practice how a SOC analyst reviews logs, checks event details, validates affected systems, and documents findings.

---

## Skills Demonstrated

- Windows security log analysis
- Event Viewer monitoring
- Active Directory account monitoring
- Wazuh SIEM deployment
- Wazuh agent configuration
- Centralized log monitoring
- Failed logon detection
- Account lockout investigation
- Sysmon endpoint monitoring
- Windows Firewall logging
- Windows Filtering Platform event review
- Kali Linux network testing
- Nmap scanning
- Wireshark packet analysis
- HTTP traffic analysis
- Basic incident response documentation
- Blue-team/SOC fundamentals
- Technical documentation using GitHub

---

## Project Status

Completed.

---

## Resume Summary

Built and expanded a basic SOC/SIEM security monitoring lab using Wazuh, Ubuntu Server, Windows Server 2022, Windows 10 endpoints, Sysmon, Kali Linux, Nmap, and Wireshark. Configured Wazuh agents to collect Windows security logs and detect failed logons, user account creation, account lockout, account unlock, account changes, and security log clearing events. Performed basic network traffic testing and packet analysis, then documented all findings and screenshots in GitHub.

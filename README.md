# Basic SOC / SIEM Security Monitoring Lab

## Project Overview
This project documents a basic Security Operations Center (SOC) and SIEM security monitoring lab using Windows Event Viewer and Wazuh SIEM.

The lab started with local Windows security log monitoring using Event Viewer, then expanded into centralized log monitoring using Wazuh SIEM. The project focuses on detecting failed logons, successful logons, user account creation, account lockout, and account unlock events.

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
- Document security findings and incident response results

---

## Lab Environment

| Device | Role | Operating System | IP Address | Purpose |
|---|---|---|---|---|
| Wazuh-Server | SIEM Server | Ubuntu Server 24.04 LTS | 192.168.10.50 | Collects and analyzes security logs |
| Server2022 | Domain Controller / Wazuh Agent | Windows Server 2022 | 192.168.10.10 | Generates domain and account security events |
| Desktop1 | Windows Endpoint / Wazuh Agent | Windows 10 Pro | 192.168.10.x | Generates Windows logon events |
| Kali-Linux | Testing Machine | Kali Linux | 192.168.10.x | Optional testing machine for later activities |

---

## Tools Used
- Wazuh SIEM
- Ubuntu Server 24.04 LTS
- Windows Server 2022
- Windows 10 Pro
- Windows Event Viewer
- Windows Security Logs
- Active Directory Users and Computers
- Command Prompt
- PowerShell
- VirtualBox

---

## Key Security Events

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4740 | User account locked out |
| 4767 | User account unlocked |

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

## Documentation
- [Lab Environment](documentation/lab-environment.md)
- [Security Event IDs](documentation/security-event-ids.md)
- [Incident Report](documentation/incident-report.md)
- [Testing Results](documentation/testing-results.md)
- [Troubleshooting Notes](documentation/troubleshooting-notes.md)

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
- Basic incident response documentation
- Blue-team/SOC fundamentals
- Technical documentation using GitHub

---

## Project Status
Completed.

---

## Resume Summary
Built and expanded a basic SOC/SIEM security monitoring lab using Wazuh, Ubuntu Server, Windows Server 2022, and Windows 10 endpoints. Configured Wazuh agents to collect Windows security logs and detect failed logons, user account creation, account lockout, and account unlock events. Documented security findings, screenshots, and incident response workflow in GitHub.

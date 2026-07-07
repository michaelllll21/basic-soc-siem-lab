# Basic SOC / Security Monitoring Lab

## Project Overview
This project documents a basic Security Operations Center (SOC) and security monitoring lab built using a virtual Windows environment. The lab focuses on monitoring Windows security events, identifying failed and successful logins, reviewing important event IDs, and documenting basic incident response findings.

This lab is designed to build foundational blue-team cybersecurity skills for entry-level IT support, cybersecurity, and SOC analyst roles.

## Objectives
- Build a basic security monitoring lab environment
- Review Windows Security logs using Event Viewer
- Identify failed login attempts
- Identify successful login events
- Understand common Windows security event IDs
- Document findings in a basic incident report
- Practice security monitoring and investigation workflow
- Prepare for future SIEM tools such as Wazuh or Microsoft Sentinel

## Lab Environment

| Device | Role | Operating System | Purpose |
|---|---|---|---|
| Server2022 | Domain Controller | Windows Server 2022 | Domain services and user management |
| Desktop1 | Domain Client | Windows 10 | Security event generation and monitoring |
| Kali-Linux | Testing Machine | Kali Linux | Optional network testing in later phase |

## Tools Used
- Windows Event Viewer
- Windows Security Logs
- Command Prompt
- PowerShell
- Active Directory Users and Computers
- VirtualBox
- Windows Server 2022
- Windows 10

## Key Security Events

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4634 | Account logoff |
| 4720 | User account created |
| 4725 | User account disabled |
| 4726 | User account deleted |
| 4740 | User account locked out |
| 4732 | User added to a security-enabled local group |

## Lab Activities
- Generated failed login attempts
- Located failed login events in Event Viewer
- Verified successful login events
- Reviewed domain user account activity
- Detected user account creation
- Detected account lockout activity
- Documented findings in a basic incident report

## Documentation
- [Lab Environment](documentation/lab-environment.md)
- [Security Event IDs](documentation/security-event-ids.md)
- [Incident Report](documentation/incident-report.md)
- [Testing Results](documentation/testing-results.md)
- [Troubleshooting Notes](documentation/troubleshooting-notes.md)

## Evidence Screenshots

### Event Viewer Security Log
![Event Viewer Security Log](screenshots/01-event-viewer-security-log.png)

### Failed Logon Event - 4625
![Failed Logon Event 4625](screenshots/02-failed-logon-event-4625.png)

### Successful Logon Event - 4624
![Successful Logon Event 4624](screenshots/03-successful-logon-event-4624.png)

### User Account Created Event - 4720
![User Created Event 4720](screenshots/04-user-created-event-4720.png)

### Account Locked Out Message
![Account Locked Out Message](screenshots/05-account-locked-out-login-message.png)

### Account Lockout Event - 4740
![Account Lockout Event 4740](screenshots/06-account-lockout-event-4740.png)

### Account Unlock Verification
![Account Unlock Verification](screenshots/07-unlock-account-aduc.png)

## Phase 2: Wazuh SIEM Monitoring

This phase expands the lab by deploying Wazuh SIEM to collect and monitor Windows security logs from domain endpoints.

### Wazuh Lab Environment

| Device | Role | IP Address | Purpose |
|---|---|---|---|
| Wazuh-Server | Wazuh SIEM Server | 192.168.10.50 | Collects and analyzes security logs |
| Server2022 | Domain Controller / Wazuh Agent | 192.168.10.10 | Generates domain security events |
| Desktop1 | Windows Endpoint / Wazuh Agent | 192.168.10.x | Generates Windows logon events |

### Wazuh Monitoring Activities

- Installed and configured Wazuh Server on Ubuntu Server
- Added Windows 10 Desktop1 as a Wazuh agent
- Added Windows Server 2022 Domain Controller as a Wazuh agent
- Detected failed logon events using Event ID 4625
- Detected user account creation using Event ID 4720
- Detected account lockout using Event ID 4740
- Detected account unlock using Event ID 4767
- Reviewed alerts through Wazuh Threat Hunting

### Wazuh Evidence Screenshots

#### Wazuh Agents Active
![Wazuh Agents Active](screenshots/13-wazuh-agents-desktop1-server2022-active.png)

#### Wazuh Agent | 192. Failed Logon Event - 4625
![Wazuh Failed Logon 4625](screenshots/15-wazuh-failed-logon-4625-filtered.png)

#### User Account Created - 4720
![Wazuh User Created 4720](screenshots/16-wazuh-user-created-4720.png)

#### Account Lockout - 4740
![Wazuh Account Lockout 4740](screenshots/17-wazuh-account-lockout-4740.png)

#### Account Unlock - 4767
![Wazuh Account Unlock 4767](screenshots/18-wazuh-account-unlocked-4767.png)

## Project Status
Completed.

## Resume Summary
Built and documented a basic SOC/security monitoring lab using Windows Event Viewer, Windows Security logs, failed logon events, successful logon events, user account creation events, account lockout events, and incident documentation. Practiced identifying security-related Windows Event IDs and creating basic incident response documentation.

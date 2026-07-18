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
- Detected user added to security group
- Detected cleared Windows Security log event
- Verified events in both Event Viewer and Wazuh

### Additional Security Events

| Event ID | Meaning |
|---|---|
| 4724 | Password reset attempted |
| 4725 | User account disabled |
| 4722 | User account enabled |
| 4728 | User added to security-enabled global group |
| 1102 | Windows Security log cleared |

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

In this phase, Windows Security and Microsoft Defender were reviewed as part of endpoint security monitoring. A PowerShell recon test was also performed to generate endpoint activity for monitoring.

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

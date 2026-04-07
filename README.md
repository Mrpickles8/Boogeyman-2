# Boogeyman-2

## Objective
Investigate a phishing-led intrusion on a corporate Windows environment. The challenge covered the full attack chain from malicious document delivery through macro execution, to C2 establishment, credential dumping, and lateral movement.

### Skills Learned
- Malicious macro and VBA code analysis
- C2 beacon identification in network logs
- Credential dumping detection (LSASS access)
- Lateral movement tracking via Windows event logs
- Multi-source log correlation (Sysmon, network, Windows Security)
- MITRE ATT&CK multi-tactic mapping

### Tools Used
- Sysmon (process creation, network connections, file events)
- Windows Security Event Logs
- Wireshark / PCAP analysis
- MITRE ATT&CK framework
- Timeline Explorer

## Steps
The investigation started with identifying the malicious document that served as the initial access vector, analyzing the macro code within. Sysmon Event ID 1 revealed the child process spawned post-macro execution, confirming code execution. Network logs were analyzed to identify the C2 callback. LSASS access events (Sysmon Event ID 10) confirmed credential dumping attempts. Lateral movement was tracked via Event ID 4624 logon events from the compromised host to adjacent machines. The complete kill chain was reconstructed and mapped to MITRE ATT&CK.

*Ref 1: Sysmon Event ID 1 showing malicious child process spawned by Office macro*
*Ref 2: Event ID 4624 logon chain confirming lateral movement to target workstation*

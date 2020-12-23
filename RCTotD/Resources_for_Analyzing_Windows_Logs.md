# Random Cybersecurity Tip of the Day
### Resources for Analyzing Windows Logs

Of course Microsoft's own site is a good first place to check. You can either just google the event ID, like "Event ID 4625" or go here: [https://docs.microsoft.com/](https://docs.microsoft.com/) to search and then you'll land on a page like this: [https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4625](https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4625)

Windows Security Event Log Encyclopedia: [https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/)

Cheat Sheets for setting up Windows Logging: [https://www.malwarearchaeology.com/cheat-sheets/](https://www.malwarearchaeology.com/cheat-sheets/)

Applied Incident Response - "Windows Event Log Reference": [http://www.appliedincidentresponse.com/windows-event-log-analyst-reference](http://www.appliedincidentresponse.com/windows-event-log-analyst-reference)

SANS Blue Team Wiki - Windows Event Log Table: [https://wiki.sans.blue/#!Tools/WindowsEventLogsTable.md](https://wiki.sans.blue/#!Tools/WindowsEventLogsTable.md)

Whether you use NXLog or not, they have great documentation on Windows Event Logs/IDs:
- Whole section on Windows Event Logs: [https://nxlog.co/documentation/nxlog-user-guide/windows-eventlog.html](https://nxlog.co/documentation/nxlog-user-guide/windows-eventlog.html)
- Specific Event IDs to focus on: [https://nxlog.co/documentation/nxlog-user-guide/eventlog-eventids.html](https://nxlog.co/documentation/nxlog-user-guide/eventlog-eventids.html)

NSA Deep Dive: "Spotting the Adversary with Windows Event Log Monitoring" [https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)

Site From JPCert that shows Event Log evidence of attacker tools after they've infiltrated the network: [https://jpcertcc.github.io/ToolAnalysisResultSheet/](https://jpcertcc.github.io/ToolAnalysisResultSheet/)

Two fantastic open source projects doing work with mapping Windows Event Logs to Mitre ATT&CK Techniques:
- [https://github.com/mitre-attack/attack-datasources](https://github.com/mitre-attack/attack-datasources) by Jamie Williams, Jose Rodriguez, and Adam Pennington
- [https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES](https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES) by Samir Bousseaden
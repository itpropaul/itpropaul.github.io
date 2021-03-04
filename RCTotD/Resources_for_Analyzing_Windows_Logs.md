<div align="center"><h1>Random Cybersecurity Tip of the Day</h1></div>
<div align="center"> <i>12/24/2020 - Paul Masek</i> </div>

### Resources for Analyzing Windows Logs

Of course Microsoft's own site is a good first place to check. You can either just google the event ID, like "Event ID 4625" or go here: <https://docs.microsoft.com/> to search and then you'll land on a page like this: <https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4625>

Windows Security Event Log Encyclopedia: <https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/>

Cheat Sheets for setting up Windows Logging: <https://www.malwarearchaeology.com/cheat-sheets/>

Applied Incident Response - "Windows Event Log Reference": <http://www.appliedincidentresponse.com/windows-event-log-analyst-reference>

SANS Blue Team Wiki - Windows Event Log Table: <https://wiki.sans.blue/#!Tools/WindowsEventLogsTable.md>

Whether you use NXLog or not, they have great documentation on Windows Event Logs/IDs:
- Whole section on Windows Event Logs: <https://nxlog.co/documentation/nxlog-user-guide/windows-eventlog.html>
- Specific Event IDs to focus on: <https://nxlog.co/documentation/nxlog-user-guide/eventlog-eventids.html>

NSA Deep Dive: "Spotting the Adversary with Windows Event Log Monitoring" <https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm>

Site From JPCert that shows Event Log evidence of attacker tools after they've infiltrated the network: <https://jpcertcc.github.io/ToolAnalysisResultSheet/>

Two fantastic open source projects doing work with mapping Windows Event Logs to Mitre ATT&CK Techniques:
- <https://github.com/mitre-attack/attack-datasources> by Jamie Williams, Jose Rodriguez, and Adam Pennington
- <https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES> by Samir Bousseaden

[Update 12/30/2020]<br>
In a similar vein to the last resource, the following resource from Forward Defense discusses common attacker techniques/tools to laterally move through an environment and the Windows Event Log evidence of how to detect that activity. <https://www.forwarddefense.com/pdfs/Lateral-Movement-Analysis.pdf>

[Update 3/4/2021]<br>
A relatively new resource to this realm of Windows Logging resources is a site called <https://what2log.com>. I first discovered it from this SANS webcast titled, [Life is a Bit Easier with What2Log.com | Mick Douglas & Flynn Weeks](https://youtu.be/JSEGfYsP7zQ). <br>
They are admittedly light on content as it's new, but what they do have is looking great so far. The site's format is very approachable.<br>
In a nutshell they teach what to log, why, and how to capture said logs. They also have a great blog.
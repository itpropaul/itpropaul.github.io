<div align="center"><h1>Random Cybersecurity Tip of the Day</h1></div>
<div align="center"> <i>12/14/2020 - Paul Masek</i> </div>

### PowerShell for Windows Event Log Analysis

In this example I'm just looking at the destination IP addresses in all of the recorded network connections and grouping them together. Once grouped together, then I'm sorting them from most frequent to least. This example is Sysmon Event 3 (Network Connection), but the same method will apply to other Windows Event logs.
```
(Get-WinEvent -Path "c:\sysmon.evtx" -FilterXPath '*/*/EventID=3' | 
Format-List message | 
Out-String).Split([Environment]::NewLine).Trim() |
Select-String DestinationIp |Group-Object -NoElement |
Sort-Object count -Descending |Format-Table -AutoSize
```
There's a decent amount of magic dust in here which I'll explain in my [next post](https://paul-masek.com/RCTotD/PowerShell_for_Windows_Event_Log_Analysis_Explained).
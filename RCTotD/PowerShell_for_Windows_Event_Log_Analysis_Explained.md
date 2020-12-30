<div align="center"><h1>Random Cybersecurity Tip of the Day</h1></div>
<div align="center"> <i>12/17/2020 - Paul Masek</i> </div>

### PowerShell for Windows Event Log Analysis Explained

This is a continuation of my most recent post: [PowerShell for Windows Event Log Analysis](https://paul-masek.com/RCTotD/PowerShell_for_Windows_Event_Log_Analysis). In today's article, I'm going to break down the script and explain as I go.

```
(Get-WinEvent -Path c:\sysmon.evtx -FilterXPath 'Event/System/EventID=3' | 
Select-Object -ExpandProperty Message).split([Environment]::NewLine) |
Select-String DestinationIP |
Group-Object -NoElement |
Sort-Object count -Descending |
Format-Table -AutoSize
```

>Note: You'll see minor changes from the original script versus today's example. While they both accomplish the same goal, this one is a little cleaner and forgoes the need to use the Out-String cmdlet and the .trim() string method.

>Note Round 2: In order to get the most out of this article, I highly recommend you follow along. In order to follow along you'll need to have a machine handy that has Sysmon installed and is capturing network events. More about Sysmon here: https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon. Read about a Symon config I like, use, and have contributed a little to here: https://github.com/SwiftOnSecurity/sysmon-config.

### ```Get-WinEvent -Path c:\sysmon.evtx```

Get-WinEvent = Gets events from Windows event logs. You can directly query the logs on the machine you're on by doing a command like: ```Get-WinEvent -LogName Security```. Or you can query the Windows event log files by path, which allows you to get them from a remote computer and analyze on yours. For Vista/2008 and newer, you'll find the evtx files here: C:\Windows\System32\winevt\Logs\

### ```-FilterXPath 'Event/System/EventID=3'```

-FilterXPath = There's a saying from Don Jones in the PowerShell community, "filter left, format right". The rationale behind this is that our script will finish much faster and be more efficient on system/network resources if PowerShell gets handed, via the pipeline, a smaller dataset to process. In my example we're narrowing down to Sysmon Event ID 3. You could get much more granular though, with -FilterXPath you could filter all the way down to a specific TargetUserName in security logon events (4624) like this: ```Get-WinEvent -LogName Security -FilterXPath 'Event/System/EventID=4624 and Event/EventData/Data[@Name="TargetUserName"]="testuser"'```

### ```| Select-Object -ExpandProperty Message```

Now that we have Sysmon Event ID 3 events, let's keep refining our data. Looking at the full contents of just one of these events fills up my screen as I'm looking at 27 properties. This is where we start piping. I only care about the Destination IP address and that value is contained within the Message property. I use the Select-Object cmdlet to just grab the Message property, but further for the remainder of the script I only want string data, not PowerShell objects, so I can use the -ExpandProperty parameter to pipe out just the string value.

### ```(...).split([Environment]::NewLine)```

This is where things get more interesting. Due to how Windows Event Logs are formatted, the meat of the events is contained within this Message property. So we now have to do further extracting from the 19 lines of information within that Message property. In order to break the Message property up, we're going to split it up based on line breaks, this allows us to separate out the data we care about from the rest of those other 18 lines. To split it up we encapsulate our current script in parenthesis and then call the split string method on that PowerShell data. Within our split method, we instruct PowerShell to split on new lines. Split could also be used to split on something simpler like a comma, ```.split(',')```.

### ```| Select-String DestinationIP```

We select just the DestinationIP values with Select-String, which is essentially Grep for PowerShell.

### ```| Group-Object -NoElement```

We group together all of the matching values and show the number of times those values occur with Group-Object and hide redundant info in this case with the -NoElement parameter.

### ```| Sort-Object count -Descending ```

We sort our grouped lines of Destination IP addresses by those occurring most frequently to least.

### ```| Format-Table -AutoSize```

Lastly, we use the Format-Table cmdlet with the -AutoSize parameter to ensure that our output doesn't get abbreviated automatically by PowerShell.

---

References: <br>
Get-WinEvent -FilterXPath ideas - [https://materials.rangeforce.com/tutorial/2020/03/03/Windows-Logging/](https://materials.rangeforce.com/tutorial/2020/03/03/Windows-Logging/)

"filter left, format right" - [https://docs.microsoft.com/en-us/previous-versions/technet-magazine/ee361592(v=msdn.10)](https://docs.microsoft.com/en-us/previous-versions/technet-magazine/ee361592(v=msdn.10))

Get-WinEvent -FilterXPath with multiple values examples - [https://powershell.org/2019/08/a-better-way-to-search-events/](https://powershell.org/2019/08/a-better-way-to-search-events/)

Splitting on new lines - [https://stackoverflow.com/a/39252621/1078245](https://stackoverflow.com/a/39252621/1078245)

Select-Object -ExpandProperty parameter to output just the string value - [https://devblogs.microsoft.com/powershell/select-expandproperty-propertyname/](https://devblogs.microsoft.com/powershell/select-expandproperty-propertyname/)
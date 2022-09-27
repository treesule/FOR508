WMI allow triggers (filters) to be set that when satisfied will run scripts or executables <br />
 
1. Event Filter --> Trigger condition <br />
2. Event Consumer --> script or executable to run <br />
3. Binding --> Tie together Filter + Comsumer <br />

•	Filter can be based on time (every 20 sec), service start, user auth file creation, etc <br />
•	Powershel or mofcomp.exe can be used to setup <br />
•	The below powershell commands can be used to identify wmic entries <br />

PowerShell contain cmdlets that can query WMI objects and retrieve information back to the console. The following commands can be used to validate that the arbitrary events have been created and the malicious payload/command is stored in the WMI repository <br />

Get-WMIObject -Namespace root\Subscription -Class __EventFilter <br />
Get-WMIObject -Namespace root\Subscription -Class __FilterToConsumerBinding <br />
Get-WMIObject -Namespace root\Subscription -Class __EventConsumer <br />

ref: https://www.ired.team/offensive-security/persistence/t1084-abusing-windows-managent-instrumentation <br />

The .MOF file was auto-compiled by the system to creat a wmic evet filer and consumer to immediately execute the task for example a script ot executable.

ForEach ($NameSpace in "root\subscription","root\default") { get-wmiobject -namespace $NameSpace -query "select * from __EventConsumer" }


**wmic PROCESS WHERE "NOT ExecutablePath LIKE '%Windows%'" GET ParentProcessId ProcessId Description ExecutablePath**

**wmic /user:#{user_name} /password:#{password} /node:"#{node}" process call create #{process_to_execute}**

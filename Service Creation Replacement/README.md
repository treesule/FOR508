
what is the difference between service and process in windows  <br />
A process is an instance of a particular executable (.exe program file) running  <br />

A service is a process which runs in the background and does not interact with the desktop  <br />

Examples:

List the services running under each process:

TASKLIST /svc

List the services running under each SvcHost process:

TASKLIST /FI "imagename eq svchost.exe" /svc

List the services running now:

TASKLIST /v /fi "STATUS eq running"

List the services with an ImageName that starts with "C" - notice that a wildcard can only be used at the end of the string:

TASKLIST /FI "IMAGENAME eq c*"

List the services running under a specific user account:

TASKLIST /v /fi "username eq SERVICE_ACCT05"

“Here's to the success of our impossible task!” ~ Soviet dissidents, 1975

Related commands:

Query Process - Display processes (TS/Remote Desktop).
PsList - List detailed information about processes.
TLIST - Task list with full path.
MSINFO32 - Windows System Information.
WMIC /OUTPUT:C:\demo\procs.txt PROCESS get Caption,Commandline,Processid
Equivalent PowerShell: Get-Process - Get a list of processes on a machine (ps/gps).
Equivalent bash command (Linux): ps - Process status, information about processes running in memory.

ⓘ

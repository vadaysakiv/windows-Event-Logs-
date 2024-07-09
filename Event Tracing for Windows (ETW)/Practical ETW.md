Example of unusual realtion between the child and parent process 
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/c8fe2e8a-553a-42cc-a2d5-ecc847cc41d7)

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/d89f2981-f66f-4e4d-80d5-fd0cf6b3c931)

like this its not usual to see cmd realted to spoolsv.exe

**
to detect parent PID spoofing **

PS C:\Tools\psgetsystem> powershell -ep bypass
PS C:\Tools\psgetsystem> Import-Module .\psgetsys.ps1 
PS C:\Tools\psgetsystem> [MyProcess]::CreateProcessFromParent([Process ID of spoolsv.exe],"C:\Windows\System32\cmd.exe","")
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/53a23faf-f579-479a-8a38-e51d7a9979af)




2nd method
collecting data from the Microsoft-Windows-Kernel-Process provider using SilkETW

c:\Tools\SilkETW_SilkService_v8\v8\SilkETW>SilkETW.exe -t user -pn Microsoft-Windows-Kernel-Process -ot file -p C:\windows\temp\etw.json
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/31455f9b-6277-4fdb-84f6-78ce5c650b1d)
The etw.json file (that includes data from the Microsoft-Windows-Kernel-Process provider) seems to contain information about powershell.exe being the one who created cmd.exe.

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/cf8160e3-e05c-42cb-8404-72a79323278a)




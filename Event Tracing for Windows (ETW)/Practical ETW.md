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


Detection Example 2: Detecting Malicious .NET Assembly Loading

For demonstrative purposes, let's emulate a malicious .NET assembly load by executing a precompiled version of Seatbelt that resides on disk. Seatbelt is a well-known .NET assembly, often employed by adversaries who load and execute it in memory to gain situational awareness on a compromised system.
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/4d8a4000-9958-46f4-8f15-06ab0b6542a8)

Assuming we have Sysmon configured appropriately to log image loading events (Event ID 7), executing 'Seatbelt.exe' would trigger the loading of key .NET-related DLLs such as 'clr.dll' and 'mscoree.dll'. Sysmon, keenly observing system activities, will log these DLL load operations as Event ID 7 records.
to start sysmon:  sysmon.exe -i -accepteula -h md5,sha256,imphash -l -n

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/f7d9ae33-edf4-43ea-8bf9-044b17fb1d5a)


![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/9e9a1730-53fc-46e2-beef-ef1c35dee646)
Let's use SilkETW to collect data from the Microsoft-Windows-DotNETRuntime provider.

c:\Tools\SilkETW_SilkService_v8\v8\SilkETW>SilkETW.exe -t user -pn Microsoft-Windows-DotNETRuntime -uk 0x2038 -ot file -p C:\windows\temp\etw.json
The etw.json file (that includes data from the Microsoft-Windows-DotNETRuntime provider) seems to contain a wealth of information about the loaded assembly, including method names.

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/1582ca72-3578-4307-a474-6a8d22ac1abd)

for the question for practical searching mangedinteropmethodname in the file 

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/f13fb580-64ce-410a-aec7-533366860920)

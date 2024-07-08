We can do that by utilizing the PSInject project in the following manner.

  Analyzing Evil With Sysmon & Event Logs
 powershell -ep bypass
 Import-Module .\Invoke-PSInject.ps1
 Invoke-PSInject -ProcId [Process ID of spoolsv.exe] -PoshCode "V3JpdGUtSG9zdCAiSGVsbG8sIEd1cnU5OSEi"
 ![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/bcfc17bc-b463-43e9-8b2b-3ed4e42149a9)
After the injection, we observe that "spoolsv.exe" transitions from an unmanaged to a managed state.
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/7b6c652f-d337-4ef9-ba9b-a90934bf86a3)

Additionally, by referring to both the related "Modules" tab of Process Hacker and Sysmon Event ID 7, we can examine the DLL load information to validate the presence of the aforementioned DLLs.
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/b5ecbbda-8121-4ac5-82ae-2391f01925dc)
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/40eb2ba3-f54c-4929-ab19-9a237cece60a)

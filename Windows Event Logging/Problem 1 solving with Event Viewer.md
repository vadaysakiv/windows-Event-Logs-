


since ID 4624 mean it realted to SUCCESSFUL LOGON
to perform this here are is the steps i used


1- open the event viewer

2- in event viewer navigating to Windows Logs --> Security 

3- in filter Current Log type event code 4624 and using the timestamp of date 8 march 2022 and using random time as i will search the time manually on that date

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/c3e3053e-4e7c-42a1-8c6c-208922e33efd)
provided time 1 minute extra than target to get extra info 

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/00dc57fd-a3f5-4921-9776-cb1292f0f9c5)
i have found the app used on that timeline which is 
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/48f5f64c-c0db-4937-a42f-f69dc6ae24fa)
now to see the changes on object done by this process , event code 4907 because  the analysis begins with Event ID 4907, which signifies an audit policy change.
creating
4- noting the value of SubjectLogonID- 0x3e7
5- now creating custom xml to search for SubjectLogonID- 0x3e7 and Event ID 4907
6- Search for the time after 10:23:25 which in this case is 10:23:49 coz 49 was the first event after 25th second 
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/fbfb7be7-c03d-4fb7-b71d-d2dff6be47ce)
this is the process name which was affected by the LogonID-0x3e7 




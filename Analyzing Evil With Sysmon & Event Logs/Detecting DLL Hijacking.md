By examining the modified configuration, we can observe that the "include" comment signifies events that should be included.

![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/45c594cb-4867-4b97-ae1f-09beff15ade1)

In the case of detecting DLL hijacks, we change the "include" to "exclude" to ensure that nothing is excluded, allowing us to capture the necessary data.
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/dcf2b430-f1b2-4c39-b5cc-ec8f21a64ff0)

To view these events, navigate to the Event Viewer and access "Applications and Services" -> "Microsoft" -> "Windows" -> "Sysmon." A quick check will reveal the presence of the targeted event ID.



Let's now see how a Sysmon event ID 7 looks like.
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/f78a8425-af59-4c7b-ab9b-2ed6d9ab9aae)


list of DLL Hijack techniques: https://www.wietzebeukema.nl/blog/hijacking-dlls-in-windows
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/fba6d3b2-31c1-468d-9c9b-2d0db3ce22c1)

for this task using reflective dll:https://github.com/stephenfewer/ReflectiveDLLInjection/tree/master/bin

trying to hijack calc.exe by coping it from system32 to any writable directory and copying the reflective_dll.x64.dll to that directory
now when we open the calc.exe it will show 
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/d29d1171-42eb-454e-b18b-02736b97d13e)


to monitor this event use  the code 7 in event viewer
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/a509cdc2-7c09-4e03-920f-36c878a75cc2)
![image](https://github.com/vadaysakiv/windows-Event-Logs-/assets/90182273/a99ea413-528e-4d23-9792-cbaa01096908)



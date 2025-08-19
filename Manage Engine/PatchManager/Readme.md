# Reset two-factor
```
cd c:\Program Files\UEMS_CentralServer\bin\ExecuteQuery.bat disable2FA.xml
```
<img width="667" height="471" alt="image" src="https://github.com/user-attachments/assets/f0fc7105-9c84-4d50-b767-b2d840891802" />

# install agnet 
download agent and share it for everyone
```
msiexec /i "\\ServerPath\UEMSAgent.msi" /qn TRANSFORMS="UEMSAgent.mst" ENABLESILENT=yes REBOOT=ReallySuppress INSTALLSOURCE=Manual SERVER_ROOT_CRT="%cd%\DMRootCA-Server.crt" DS_ROOT_CRT="%cd%\DMRootCA.crt" /l*v "C:\Agentinstalllog.txt
```
- batch file
```
@echo off
setlocal

set "Source=\\file\Softbank\EndPointCentral\faradis-agent\msi"
set "TempPath=%TEMP%\EndPointCentral"

xcopy "%Source%" "%TempPath%" /E /I /Y /H



set "MsiPath=%TempPath%\UEMSAgent.msi"
set "MstPath=%TempPath%\UEMSAgent.mst"
set "LogPath=C:\Agentinstalllog.txt"

msiexec /i "%MsiPath%" /qn TRANSFORMS="%MstPath%" ENABLESILENT=yes REBOOT=ReallySuppress INSTALLSOURCE=Manual SERVER_ROOT_CRT="%cd%\DMRootCA-Server.crt" DS_ROOT_CRT="%cd%\DMRootCA.crt" /l*v "%LogPath%"


rmdir /s /q "%TempPath%"

endlocal
```

# uninstall
show Product Code
```
Get-WmiObject Win32_Product | Where-Object { $_.Name -like "*ManageEngine*" } | Select-Object Name, IdentifyingNumber
```

<img width="1030" height="79" alt="image" src="https://github.com/user-attachments/assets/e6652245-bd14-4d0d-ae67-909b544a83a3" />


```
msiexec /x {6AD2231F-FF48-4D59-AC26-405AFAE23DB7} /qn
```
# Ports
- Https Agents to Distribution server
    * 8027,8383 agent to server
- Https Agents to server 
    * 8084 agent to Distribution server

- distribution server to server
    * 8020,8027,8384 Distribution server to server

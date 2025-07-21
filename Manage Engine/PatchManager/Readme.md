## Reset two-factor
```
cd c:\Program Files\UEMS_CentralServer\bin\ExecuteQuery.bat disable2FA.xml
```
<img width="667" height="471" alt="image" src="https://github.com/user-attachments/assets/f0fc7105-9c84-4d50-b767-b2d840891802" />

## install agnet 
download agent and share it for everyone
```
msiexec /i "\\ServerPath\UEMSAgent.msi" /qn TRANSFORMS="UEMSAgent.mst" ENABLESILENT=yes REBOOT=ReallySuppress INSTALLSOURCE=Manual SERVER_ROOT_CRT="%cd%\DMRootCA-Server.crt" DS_ROOT_CRT="%cd%\DMRootCA.crt" /l*v "C:\Agentinstalllog.txt
```
#### uninstall
```
msiexec /x {6AD2231F-FF48-4D59-AC26-405AFAE23DB7} /qn
```

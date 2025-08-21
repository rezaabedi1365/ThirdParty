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
 
## Check version > uninstall old versioin > install new version
```
@echo off
echo چک کردن نسخه Endpoint Central Agent ...
reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" | find "DisplayVersion"
reg query "HKLM\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" | find "DisplayVersion"

reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Desktop Central" | find "DisplayVersion"
reg query "HKLM\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Desktop Central" | find "DisplayVersion"
pause

```

```
@echo off
setlocal

REM مسیر فایل نصب نسخه جدید
set "Source=\\file\Softbank\EndPointCentral"
set "MsiPath=%TEMP%\EndPointCentral\UEMSAgent.msi"
set "MstPath=%TEMP%\EndPointCentral\UEMSAgent.mst"
set "LogPath=C:\Agentinstalllog.txt"

REM ------------------------
REM 1) پیدا کردن ورژن فعلی
REM ------------------------
for /f "tokens=2*" %%A in ('reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" ^| find "DisplayVersion"') do set "Version=%%B"
if not defined Version (
  for /f "tokens=2*" %%A in ('reg query "HKLM\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" ^| find "DisplayVersion"') do set "Version=%%B"
)

echo نسخه نصب‌شده فعلی: %Version%

REM ------------------------
REM 2) بررسی شرط
REM ------------------------
if "%Version%"=="1" (
    echo نسخه 1 پیدا شد. حذف و نصب نسخه جدید...
    
    REM حذف نسخه قبلی
    for /f "tokens=2*" %%A in ('reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" ^| find "UninstallString"') do set "UninstallCmd=%%B"
    if not defined UninstallCmd (
        for /f "tokens=2*" %%A in ('reg query "HKLM\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall" /s /f "Endpoint Central" ^| find "UninstallString"') do set "UninstallCmd=%%B"
    )

    if defined UninstallCmd (
        echo اجرای حذف: %UninstallCmd%
        call %UninstallCmd% /qn REBOOT=ReallySuppress
    )

    REM کپی نسخه جدید به TEMP
    if exist "%TEMP%\EndPointCentral" rmdir /s /q "%TEMP%\EndPointCentral"
    mkdir "%TEMP%\EndPointCentral"
    xcopy "%Source%" "%TEMP%\EndPointCentral" /E /I /Y /H

    REM نصب نسخه جدید
    msiexec /i "%MsiPath%" /qn TRANSFORMS="%MstPath%" ENABLESILENT=yes REBOOT=ReallySuppress INSTALLSOURCE=Manual /l*v "%LogPath%"

    echo ✅ نسخه جدید نصب شد. لاگ در: %LogPath%
    goto :eof
)

if "%Version%"=="2" (
    echo نسخه 2 از قبل نصبه، کاری انجام نمیشه.
    goto :eof
)

echo ❌ نسخه نصب‌شده مشخص نشد یا Agent وجود نداره.
endlocal

```



### install agent on windown
C:\zabbix\conf\zabbix_agentd.conf
```
Server=192.168.1.100
ServerActive=192.168.1.100
Hostname=MY-WINDOWS-PC
```
```
cd C:\zabbix\bin\windows\amd64
zabbix_agentd.exe --config "C:\zabbix\conf\zabbix_agentd.conf" --install
zabbix_agentd.exe --start
```

```
cd C:\zabbix\bin\windows\amd64
zabbix_agentd.exe --uninstall
```
### install with group policy

install_zabbix.bat
```
@echo off
setlocal
set ZABBIX_DIR=C:\zabbix
set SHARE=\\DC01\Deploy\Zabbix

xcopy %SHARE% %ZABBIX_DIR% /E /I /Y

rem نصب Agent
%ZABBIX_DIR%\bin\windows\amd64\zabbix_agentd.exe --config %ZABBIX_DIR%\conf\zabbix_agentd.conf --install
%ZABBIX_DIR%\bin\windows\amd64\zabbix_agentd.exe --start

rem باز کردن پورت در فایروال
netsh advfirewall firewall add rule name="Zabbix Agent" dir=in action=allow protocol=TCP localport=10050
endlocal

```

zabbix_agentd.conf
```
### Zabbix Agent Configuration File

# Server(s) allowed to connect (passive checks)
Server=192.168.1.100

# Server(s) for active checks (Agent connects to Server)
ServerActive=192.168.1.100

# Automatically use system's hostname
HostnameItem=system.hostname

# Optional: You can still set Hostname explicitly if you want
#Hostname=MY-PC-NAME

# Logging
LogFile=C:\zabbix\zabbix_agentd.log
LogFileSize=10
DebugLevel=3

# Location of PID file
PidFile=C:\zabbix\zabbix_agentd.pid

# Enable remote command execution (optional; be careful!)
EnableRemoteCommands=0
AllowKey=system.run[*]

# Allow Zabbix Server to retrieve values from this agent
ListenPort=10050

# Location of include files (if any extra configs)
Include=C:\zabbix\zabbix_agentd.conf.d\

# Timeout for agent items
Timeout=30

# Optional - For active checks, how often to refresh
RefreshActiveChecks=120

# Optional: Disable active checks
# StartAgents=0  ; if you want only active mode, set this to 0

```

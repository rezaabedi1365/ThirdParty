## install OMS WebService
Pre install
- install windows feature
```
DISM.EXE /Enable-Feature /online /featureName:IIS-WebServerRole /featureName:IIS-WebServer /featureName:IIS-CommonHttpFeatures /featureName:IIS-StaticContent /featureName:IIS-DefaultDocument /featureName:IIS-DirectoryBrowsing /featureName:IIS-HttpErrors /featureName:IIS-HttpRedirect /featureName:IIS-ApplicationDevelopment /featureName:IIS-ASPNET /featureName:IIS-NetFxExtensibility /featureName:IIS-ASPNET45 /featureName:IIS-NetFxExtensibility45 /featureName:IIS-ASP /featureName:IIS-CGI /featureName:IIS-ISAPIExtensions /featureName:IIS-ISAPIFilter /featureName:IIS-ServerSideIncludes /featureName:IIS-HealthAndDiagnostics /featureName:IIS-HttpLogging /featureName:IIS-LoggingLibraries /featureName:IIS-RequestMonitor /featureName:IIS-HttpTracing /featureName:IIS-CustomLogging /featureName:IIS-ODBCLogging /featureName:IIS-Security /featureName:IIS-BasicAuthentication /featureName:IIS-WindowsAuthentication /featureName:IIS-DigestAuthentication /featureName:IIS-ClientCertificateMappingAuthentication /featureName:IIS-IISCertificateMappingAuthentication /featureName:IIS-URLAuthorization /featureName:IIS-RequestFiltering /featureName:IIS-IPSecurity /featureName:IIS-Performance /featureName:IIS-HttpCompressionStatic /featureName:IIS-HttpCompressionDynamic /featureName:IIS-WebDAV /featureName:IIS-WebServerManagementTools /featureName:IIS-ManagementScriptingTools /featureName:IIS-ManagementService /featureName:IIS-IIS6ManagementCompatibility /featureName:IIS-Metabase /featureName:IIS-WMICompatibility /featureName:IIS-LegacyScripts /featureName:NetFx4Extended-ASPNET45 /featureName:IIS-ApplicationInit /featureName:IIS-WebSockets /featureName:IIS-CertProvider /featureName:IIS-ManagementConsole /featureName:IIS-LegacySnapIn
```
- install Microsoft .NET Core 3.1.22 - Windows Server Hosting
### Copy Smswebservice to Drive C:\

### IIS Configuration
<img width="1064" height="257" alt="image" src="https://github.com/user-attachments/assets/c001aef9-544e-4e2a-bd6c-42741d0daa09" />








<img width="660" height="494" alt="image" src="https://github.com/user-attachments/assets/7398f2a7-c85f-4239-be14-b97acbdc9ca9" />


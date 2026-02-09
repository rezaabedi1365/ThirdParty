
https://techtik.com/2017/06/13/fc-addressing/

### SAN Protocols
  - FC SAN
      * HBA Card
      * Media Fiber
      * address    
          + WWNN [World Wide Node Name]:  Specify address for Node (Device)
          + WWPN [World Wide Port Name]:  Specify address for each ports
```powershell
Get-InitiatorPort
```
<img width="949" height="318" alt="image" src="https://github.com/user-attachments/assets/2a6d53ad-bb68-458d-b9db-da58f055beb7" />
           
  - FCoE SAN [ For Short Distance ]
  
  - IP SAN (iSCSI )
      * NIC Card
      * copper 
      * address  
          + iSCSI Target [target discover ip:3260]
             -  iSCSI Initiators [IQN (iSCSI Qualified Name) iqn.YYYY-MM.com.vendor:unique_name]

  - FCIP [For Long Distance and use in WAN]
-----------------------------------------------------------------------
# SAN Switch Zonning

  - Hard Zonning
  - Soft Zonning

FC Ports
  -  F_Port  
  -  N_Port  
  -  E_Port

![image](https://github.com/user-attachments/assets/47decf01-ce6b-4db7-be77-b1ed1642a5e3)

![image](https://github.com/user-attachments/assets/a4f247db-516c-4902-84a8-cc510dc3e24a)


# Lun Mapping 

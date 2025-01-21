### VSAN Consept
Requirements
  - Hardware requirment
     + Dedicate unformat ssd . 1 ssd in hybrid mod 10%
     + Only raid 1 in hybrid and raid 1,5,10 in allflash suppurted . 
  - cluster requriment
     + if you have HA in cluster you must temporary disable it
     + 3 to 64 host
     + 5 disk group per cluster
     + 8 disk per each disk group
     + cluster sizing : calculate failure
     +   * vsan readynode sizer
         * raid 5>  2n+2
         * raid 10> 2n+3
  - software requirment
     + ESXi in cluster and vsan same version
  - network requirment
     + Dedicate NIC
     + Dedicate port group with VSAN enable
  - license requirment
     + standard
     + Advanded
     + Enterprise
         * Encryption
         * vsan storage Cluster

#### impliment
  - hybrid
  - all flash
    

-------------------------------------------------------------------
step 1 )
  - create VDS
    + add hosts to VDS
  -Seperate trafic vms , vmotion , vsan in VDS
    + assign uplink to port grroup with Teaming and failover (uplink [gig1,2] vms and uplink [gig3,4] vsan)

     

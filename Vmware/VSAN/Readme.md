### VSAN
Requirements
  - Hardware requirment
     + Dedicate unformat ssd
     + Only raid 0 suppurted . 
  - cluster requriment
     + if you have HA in cluster you must temporary disable it
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

     

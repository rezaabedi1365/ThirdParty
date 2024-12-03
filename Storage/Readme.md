# What’s the Diff: NAS vs. SAN

![image](https://github.com/user-attachments/assets/78316f2f-f601-40d4-8d83-754c987fcce1)
### SAN
* Protocols
    - FC
    - iSCSI

* Key Characteristics of SANs:
    - Block-Level Access: SANs provide direct access to storage blocks, which is advantageous for applications requiring fast, low-latency data retrieval.
    - Performance: SANs are designed to meet the rigorous demands of enterprise-level applications, ensuring reliable and high-speed data access.
    - Scalability: SANs offer greater scalability by connecting multiple storage devices, making them suitable for businesses with expanding storage needs.
    
### NAS:
* Protocols
    - SMB
    - CIFS
    - NFS

* Key Characteristics of
    - File-Level Access: NAS provides file-level access, ideal for environments where collaborative work and content sharing are paramount.
    - Simplicity: NAS solutions offer straightforward setups and intuitive interfaces, making them accessible to users with varying levels of technical expertise.
    - Scalability: While NAS devices can be expanded by adding more drives, there may be limitations in terms of performance and scalability for large-scale enterprise use.
  


# SAN Storage 
------------------------------------------------------------
### Host connectivity
   * FC    16Gb
   * iSCSI 10Gb
   * SAS   12Gb for Encluser
### Disk connector
   * SAS 12GB
   * SATA
      - SATA |    1.5Gb
      - SATA ||   3Gb
      - SATA |||  6Gb
   * USB
      - USB 1.1 12Mb
      - USB 2   480Mb
      - USB3.2  GEN1 5GB
      - USB3.2  GEN2 10Gb

 ----------------------------------------------------------
### iSCSI Presentation
Logical Volume
  * Create Pool 
      - Create Disk Group with RAID
          + create volume
          + Volume Mapping
  * add iscsi initiator
      - to Windows
      - to vmware
      - to linux
  * add target ip and discover on port 3260
----------------------------------------------------------
### FC Presentation
Requerment
  * HBA
  * VSAN 
  
 
*********************************************************************
### Hard Disk
* LFF
  - 10K , 15K
       + 146GB
       + 300GB
       + 450GB
       + 600GB
   - 5400/7200
        + 500GB
        + 1TB
        + 2TB
        + 4TB
        + 6TB
* SFF
  - 10K , 15K
       + 720
       + 146GB
       + 300GB
       + 450GB
       + 600GB
       + 900GB
       + 1200GB
   - 5400/7200
       + 1TB
    


  


----------------------------------------------------------
IPRender application for test troughput

    


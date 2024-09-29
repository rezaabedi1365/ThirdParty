
### Build numbers and versions of VMware vCenter Server
- https://knowledge.broadcom.com/external/article/326316/build-numbers-and-versions-of-vmware-vce.html
### Update Your vCenter  
- https://docs.vmware.com/en/VMware-vSphere+/services/vsphereplus-using-managing/GUID-AB325B28-A781-451E-90A6-27DABAA3B6AE.html


##### Prerequisites

- Download the latest version of the vCenter by using the Downloads option in the VMware Cloud Console. See Download Software Binaries.
- If the vCenter is in high availability (HA) mode, remove the HA configuration. After you update the vCenter, you can configure the vCenter for HA again. See Remove a vCenter HA Configuration.
- Back up your vCenter. See File-Based Backup and Restore of vCenter.

## Reduced Downtime Upgrade
- https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-vcenter-upgrade/GUID-5A9967E2-A8EC-4344-99BE-B5CB92C09E8A.html
- https://knowledge.broadcom.com/external/article/313288/vcenter-server-upgrades-with-the-reduced.html
upgrade in command-line

- Attach the VMware-vCenter-Server-Appliance-6.x-patch-FP.iso file to vCenter Server Appliance CD or DVD drive.
- Log in to the appliance shell as root and run the commands given below:
1- To stage the ISO:
        software-packages stage --iso
2- To see the staged content:
        software-packages list --staged
3- To install the staged rpms:
        software-packages install --staged

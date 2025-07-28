### Assign 4 disk in vmware
- Disk1: OS
- Disk2: /opt
- Disk3: /warmdb
- Disk4: /colddb

```
lsblk
```


### cfdisk
create new and type lvm
```
cfdisk /dev/sdb
cfdisk /dev/sdc
cfdisk /dev/sdd
```

### LVM configuration
- /opt
```
pvcreate /dev/sdb1
vgcreate opt_vg /dev/sdb1
lvcreate -l 95%FREE -n opt_lv opt_vg
mkfs.xfs /dev/opt_vg/opt_lv
```
- /warmdb
```
pvcreate /dev/sdc1
vgcreate warm_vg /dev/sdc1
lvcreate -l 95%FREE -n warm_lv warm_vg
mkfs.xfs /dev/warm_vg/warm_lv
```
- /cold
```
pvcreate /dev/sdd1
vgcreate cold_vg /dev/sdd1
lvcreate -l 95%FREE -n cold_lv cold_vg
mkfs.xfs /dev/cold_vg/cold_lv
```

### mount 
```
cd /
mkdir warmdb
mkdir colddb
```

/etc/fstab
```
/dev/mapper/opt_vg-opt_lv       /opt    xfs     defaults        0       0
/dev/mapper/warm_vg-warm_lv     /warmdb xfs     defaults        0       0
/dev/mapper/cold_vg-cold_lv     /colddb xfs     defaults        0       0
```

```
mount -a
```

verify :
```
lsblk
df -h
```

# install 
download .deb file
```
```
```
dpkg -i splunk-9.4.1-e3bdab203ac8-linux-amd64.deb
# Enter admin user and password
```

```
/opt/splunk/bin/splunk enable boot-start
/opt/splunk/bin/splunk start
```
# Basic Configuration

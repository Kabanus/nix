##### WWN list
> cat /sys/class/fc_host/host*/port_name | sed -e "s/.\\{2\\}/&\:/g" | cut -d':' -f2-9 | tr '[:lower:]' '[:upper:]'

##### Add LUN
1. > cat >> /etc/multipath.conf << EOF  
blacklist_exceptions {  
wwid **_LUN_**  
}  
EOF
2. > echo "**ALIAS** **_LUN_**" >> /etc/multipath/bindings

##### Rescan SCSI
###### Method #1
> for i in \`ls /sys/class/scsi_host/host*/scan\`; do echo "- - -" > $i; done  
###### Method #2
> rescan-scsi-bus.sh

##### Rescan LUNs
> multipath -v3
###### Check paths
> multipath -ll **ALIAS**

##### Add UDEV (Oracle ASM)
1. > echo "ENV{DM_NAME}=="**_SAN_**",SYMLINK+="oraasm/$env{DM_NAME}-**_DATABASE_**", OWNER="ora", GROUP="dba", MODE="0660"" >> /etc/udev/rules.d/99-asm-permissions.rules
2. > udevadm trigger --attr-match=subsystem=block
###### Check device
> ll /dev/oraasm/**_SAN_**-**_DATABASE_**

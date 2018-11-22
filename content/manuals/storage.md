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
> multipath -v2
###### Check paths
> multipath -ll **ALIAS**

##### Add Oracle ASM
###### Physical
> echo "ENV{DM_NAME}=="**_ALIAS_**",SYMLINK+="oraasm/$env{DM_NAME}-**_DATABASE_**", OWNER="ora", GROUP="dba", MODE="0660"" >> /etc/udev/rules.d/99-asm-permissions.rules
###### Virtual
1. > /lib/udev/scsi_id --whitelisted --device=/dev/sd**X**
2. > echo "KERNEL=="sd*", SUBSYSTEM=="block", ENV{ID_SERIAL}=="**_UUID_**", SYMLINK+="oraasm/**_DATABASE_**", OWNER="ora", GROUP="dba", MODE="0660"" >> /etc/udev/rules.d/99-asm-permissions.rules
###### Make links
> udevadm trigger --attr-match=subsystem=block
###### Check device
> ll /dev/oraasm

##### Disk usage (du) root directory (/) no recursive
> awk '{if ($2!="/") print $2}' /proc/mounts >> excludes.tmp  
> du -sh /* -X excludes.tmp | sort -h; rm -f excludes.tmp

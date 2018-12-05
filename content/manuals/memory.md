##### Memory setting for Oracle Database
- > echo "ora soft memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
- > echo "ora hard memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
- > echo "vm.nr_hugepages = $(awk '$1 == "MemTotal:"{tmp=$2/4096; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
- > echo "kernel.shmmax = $(awk '$1 == "MemTotal:"{tmp=$2\*512; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
- > echo "kernel.shmall = $(awk '$1 == "MemTotal:"{tmp=$2/2/4; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf

##### Disable Transparent Huge Pages
###### Temporary
> echo never > /sys/kernel/mm/transparent_hugepage/enabled
###### Persistent
1. > sed -i -e '/^GRUB_CMDLINE/s/"/ transparent_hugepage=never&/2' /etc/default/grub
2. > grub2-mkconfig -o /boot/grub2/grub.cfg
###### Check
> egrep AnonHugePages /proc/meminfo /proc/\*/smaps | grep -v '0 kB'

##### SWAP usage per process
```
#!/bin/bash
SUM=0
OVERALL=0
for DIR in `find /proc/ -maxdepth 1 -type d | egrep "^/proc/[0-9]"` ; do
  PID=`echo $DIR | cut -d / -f 3`
  PROGNAME=`ps -p $PID -o comm --no-headers`
    for SWAP in `grep Swap $DIR/smaps 2>/dev/null| awk '{ print $2 }'`
      do
        let SUM=$SUM+$SWAP
      done
  echo "PID=$PID - Swap used: $SUM - ($PROGNAME )"
  let OVERALL=$OVERALL+$SUM
  SUM=0
done
echo "Overall swap used: $OVERALL"
```

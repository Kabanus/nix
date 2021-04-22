##### Hewlett-Packard ILO 4 re-generate certificate
> curl -u "login:password" -k -X DELETE https://ip_address/redfish/v1/Managers/1/SecurityService/HttpsCert/

##### Hewlett-Packard ILO 4 get license key
> curl -u "login:password" -k https://ip_address/xmldata?item=CpqKey

##### Disable DSA in OpenSSH Server version 5
> mkdir /etc/ssh/dsa && mv /etc/ssh/ssh_host_dsa_key* /etc/ssh/dsa   
> sed -i -e '/^AUTOCREATE/s/YES/RSAONLY/' /etc/sysconfig/sshd   
> sed -i -e '/^#HostKey.*ssh_host_rsa_key/s/^.//' /etc/ssh/sshd_config   
> sshd -t && service sshd restart

###### Check DSA in SSHD
> nmap --script ssh2-enum-algos -p 22 localhost || sshd -T | grep ^hostkey

##### Memory setting for Oracle Database
> echo "ora soft memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
> echo "ora hard memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
> echo "vm.nr_hugepages = $(awk '$1 == "MemTotal:"{tmp=$2/4096; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
> echo "kernel.shmmax = $(awk '$1 == "MemTotal:"{tmp=$2\*512; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
> echo "kernel.shmall = $(awk '$1 == "MemTotal:"{tmp=$2/2/4; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf

##### Disable Transparent Huge Pages
###### Temporary
> echo never > /sys/kernel/mm/transparent_hugepage/enabled
###### Persistent
> sed -i -e '/^GRUB_CMDLINE/s/"/ transparent_hugepage=never&/2' /etc/default/grub   
> grub2-mkconfig -o /boot/grub2/grub.cfg
###### Check
> egrep AnonHugePages /proc/meminfo /proc/\*/smaps | grep -v '0 kB'

##### SWAP usage per process
```
#!/bin/bash
SUM=0
OVERALL=0
for DIR in `find /proc/ -maxdepth 1 -type d | egrep "^/proc/[0-9]"`; do
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
##### SWAP usage per process (mod)
```
for DIR in `find /proc/ -maxdepth 1 -type d | egrep "^/proc/[0-9]"`; do
  SUM=0
  PID=`echo $DIR | cut -d / -f 3`
  PROGNAME=`ps -p $PID -o comm,user --no-headers`
    for SWAP in `grep Swap $DIR/smaps 2>/dev/null| awk '{ print $2 }'`
      do let SUM=$SUM+$SWAP
    done
  echo "PID=$PID - Swap used: $(($SUM/1024))mb - ($PROGNAME )"
done | grep -v "Swap used: 0" | sort -n -k 5 >> swap.txt
```

##### Switch Terminal
> chvt 1

##### Copy root files
> rsync --rsync-path="sudo rsync" 10.10.10.10:/etc/kubernetes/admin.conf .

##### SSL Export
> NAME=google.com; echo | openssl s_client -servername $NAME -connect $NAME:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > certificate.crt

##### CPU
> mpstat -P ALL   
> pidstat -p <pid>   
> ps aux --sort=-pcpu | head -10   
> cpupower -c all frequency-info -p   
> cpupower -c all idle-info   

##### RAM
> ps aux --sort=-rss | head -10   
> ps aux --sort=-vsz | head -10   
> ps aux --sort=-rss | awk '{sum += $5} END {print sum}'   
> ps aux --sort=-vsz | awk '{sum += $5} END {print sum}'

##### Shared Memory
> ipcs -m   
> ipcs -mu   
> cat /proc/sysvipc/shm

##### Disk Usage (exclude /)
> awk '{print $2}' /proc/mounts | egrep -vw '^/' >> excludes.tmp; du -sh /* -X excludes.tmp | sort -h; rm -f excludes.tmp

##### Open files
> fuser -vm /dev/sdc1   
> lsof +L1

##### IOPS
> iostat -x -N 1   
> fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=fiotest --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75

##### SAR
> LANG=RU; sar -s 02:40:00 -e 03:30:00 -d -p | awk '$10>=80 {print $0}'

##### IOSTAT Veritas
```
for DG in `ls /dev/vx/dsk`;
  do for vol in `vxprint -g $DG | grep "^v " | awk '{ print $2}'`;do vxprint -g $DG $vol -F "  vol=%vol minor=%minor"; done;
done
```

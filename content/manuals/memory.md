##### Memory setting for Oracle Database
1. > echo "ora soft memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
2. > echo "ora hard memlock $(awk '$1 == "MemTotal:"{tmp=$2\*0.901; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/security/limits.conf  
3. > echo "vm.nr_hugepages = $(awk '$1 == "MemTotal:"{tmp=$2/4096; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
4. > echo "kernel.shmmax = $(awk '$1 == "MemTotal:"{tmp=$2\*512; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf  
5. > echo "kernel.shmall = $(awk '$1 == "MemTotal:"{tmp=$2/2/4; printf"%0.0f\n", tmp}' /proc/meminfo)" >> /etc/sysctl.conf

##### Disable Transparent Huge Pages
###### Temporary
> echo never > /sys/kernel/mm/transparent_hugepage/enabled
###### Persistent
1. > sed -i -e '/^GRUB_CMDLINE/s/"/ transparent_hugepage=never&/2' /etc/default/grub
2. > grub2-mkconfig -o /boot/grub2/grub.cfg
###### Check
1. > egrep AnonHugePages /proc/meminfo /proc/\*/smaps | egrep -v "0 kB"
2. > egrep AnonHugePages /proc/\*/smaps | grep -v "0 kB"

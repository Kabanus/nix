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
> sed 's/GRUB_CMDLINE_LINUX=\"/&transparent_hugepage=never /' /etc/default/grub && grub2-mkconfig -o /boot/grub2/grub.cfg
###### Check
> cat /sys/kernel/mm/transparent_hugepage/enabled && egrep AnonHugePages /proc/\*/smaps | grep -v "0 kB"

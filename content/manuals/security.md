##### Disable DSA in OpenSSH Server version 5
1. > mkdir /etc/ssh/dsa && mv /etc/ssh/ssh_host_dsa_key* /etc/ssh/dsa  
2. > sed -i -e '/^AUTOCREATE/s/YES/RSAONLY/' /etc/sysconfig/sshd  
3. > sed -i -e '/^#HostKey.\*ssh_host_rsa_key/s/^.//' /etc/ssh/sshd_config  
4. > sshd -t && service sshd restart  
###### Check SSHD
> nmap --script ssh2-enum-algos -p 22 localhost || sshd -T | grep ^hostkey

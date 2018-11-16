##### Disable DSA in OpenSSH Server version 5
- > mkdir /etc/ssh/dsa && mv /etc/ssh/ssh_host_dsa_key* /etc/ssh/dsa
- > sed -i -e '/^AUTOCREATE_SERVER_KEYS=/s/YES/RSAONLY/' /etc/sysconfig/sshd
- > sed -i -e '/^#HostKey.\*ssh_host_rsa_key/s/^.//' /etc/ssh/sshd_config
- > sshd -t && service sshd restart
###### Check SSHD
> nmap --script ssh2-enum-algos -p 22 localhost || sshd -T | grep ^hostkey

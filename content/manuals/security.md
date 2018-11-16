##### Disable DSA in OpenSSH Server version 5
- > mkdir /etc/ssh/dsa && mv /etc/ssh/ssh_host_dsa_key* /etc/ssh/dsa
- > sed -i -e 's/AUTOCREATE_SERVER_KEYS=YES/AUTOCREATE_SERVER_KEYS=RSAONLY/' /etc/sysconfig/sshd
- > sed -i -e 's/#HostKey \/etc\/ssh\/ssh_host_rsa_key/HostKey \/etc\/ssh\/ssh_host_rsa_key/' /etc/ssh/sshd_config
- > sshd -t && service sshd restart
- > nmap --script ssh2-enum-algos -p 22 localhost || sshd -T | grep ^hostkey

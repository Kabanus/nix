##### ansible
> ansible 10.0.0.1, -b -m copy -a 'src=/file dest=/file'
> ansible *inventory* -b -m shell -a 'uptime'

##### ansible-playbook
> ansible-playbook -k -b -i 10.0.0.1, script.yml

###### keys
- m // module name
- k // ask for privilege escalation password
- b // run operations with become
- i // specify inventory host path or comma separated host list

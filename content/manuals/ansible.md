##### ansible
> ansible 10.0.0.1, -b -m copy -a 'src=/file dest=/file'  
> ansible *servers* -b -m shell -a 'uptime'

###### ! [servers] from hosts
https://github.com/Kabanus/nix/blob/master/content/examples/ansible/hosts

##### ansible-playbook
> ansible-playbook -k -b -i 10.0.0.1, script.yml

###### keys
- m // module name
- k // ask for privilege escalation password
- b // run operations with become
- i // specify inventory host path or comma separated host list

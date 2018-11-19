##### WWN LIST
> cat /sys/class/fc_host/host*/port_name | sed -e "s/.\\{2\\}/&\:/g" | cut -d':' -f2-9 | tr '[:lower:]' '[:upper:]'

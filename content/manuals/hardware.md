##### Hewlett-Packard ILO 4 re-generate certificate
> curl -u "login:password" -k -X DELETE https://ip_address/redfish/v1/Managers/1/SecurityService/HttpsCert/

##### Hewlett-Packard ILO 4 get license key
> curl -u "login:password" -k https://ip_address/xmldata?item=CpqKey

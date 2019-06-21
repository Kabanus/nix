##### run image
> kubectl run APPNAME --image=REPO/NAME --port=8080 --generator=run/v1

##### expose service
> kubectl expose rc APPNAME --type=LoadBalancer --name NAME

##### scale replication controller
> kubectl scale rc NAME --replicas=NUMBER

##### cluster info
> kubectl cluster-info

##### show info
> kubectl get node|pod|rc|svc NAME|all

##### show detail
> kubectl describe node|pod|rc|svc NAME|all

###### options
* -o wide // verbose
* -o yaml // YAML

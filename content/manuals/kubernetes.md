##### run image
> kubectl run APPNAME --image=REPO/NAME --port=8080 --generator=run/v1

##### show pods
> kubectl get pods -o wide

##### pod info
> kubectl describe pod NAME

##### create service
> kubectl expose rc APPNAME --type=LoadBalancer --name NAME

##### show services
> kubectl get services -o wide

##### show all
> kubectl get all -o wide

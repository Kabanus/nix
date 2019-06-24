##### run image
> kubectl run APPNAME --image=REPO/NAME --port=8080 --generator=run/v1

##### create module
> kubectl create -f FILENAME.yaml

##### show module logs
> kubectl logs MODNAME -c CONTNAME

##### expose service
> kubectl expose rc APPNAME --type=LoadBalancer --name NAME

##### port forwarding
kubectl port-forward MODNAME LOCAL:MODULE

##### scale replication controller
> kubectl scale rc NAME --replicas=NUMBER

##### add label
> kubectl label pod NAME LABEL=VALUE

##### modify label
> kubectl label pod NAME LABEL=VALUE --overwrite

##### cluster info
> kubectl cluster-info

##### show info
> kubectl get node|pod|rc|svc NAME|all

##### show detail
> kubectl describe node|pod|rc|svc NAME|all

##### show doc
> kubectl explain node|pod|rc|svc

###### options
* -o wide // verbose
* -o yaml // YAML
* -o json // JSON
* --show-labels // labels
* -L LABEL1,LABEL2 // column per label

###### YAML
* метаданные (metadata) – включают имя, пространство имен, метки и другую информацию о модуле
* спецификация (spec) – содержит фактическое описание содержимого модуля, например контейнеры модуля, тома и другие данные
* статус (status) – содержит текущую информацию о работающем модуле, такую как условие, в котором находится модуль, описание и статус каждого контейнера, внутренний IP модуля, и другую базовую информацию

###### YAML example
```
apiVersion: v1                  # API version
kind: Pod                       # description
metadata:
  name: kubia-manual            # module name
spec:
  containers:
    - name: kubia               # container name
      image: kabanus/kubia      # image
      ports:
        - containerPort: 8080   # port
          protocol: TCP         # proto

```

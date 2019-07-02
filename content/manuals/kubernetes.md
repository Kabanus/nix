##### run image
> kubectl run APPNAME --image=REPO/NAME --port=8080 --generator=run/v1

##### create module
> kubectl create -f FILENAME.yaml

##### show module logs
> kubectl logs MODNAME -c CONTNAME

##### show previous logs
> kubectl logs PODNAME --previous

##### expose service
> kubectl expose rc APPNAME --type=LoadBalancer --name NAME

##### port forwarding
kubectl port-forward MODNAME LOCAL:MODULE

##### scale replication controller
> kubectl scale rc NAME --replicas=NUMBER

##### delete resources
> kubectl delete node|pod|rc|svc|ns NAME   
> kubectl delete pod -l creation_method=manual   
> kubectl delete all --all

##### add label
> kubectl label node|pod NAME LABEL=VALUE

##### modify label
> kubectl label pod NAME LABEL=VALUE --overwrite

##### cluster info
> kubectl cluster-info

##### show info
> kubectl get node|pod|rc|svc|ns NAME|all

##### show detail
> kubectl describe node|pod|rc|svc|ns NAME|all

##### show doc
> kubectl explain node|pod|rc|svc|ns

###### options
* -o wide // verbose
* -o yaml // YAML
* -o json // JSON
* --show-labels // labels
* -L LABEL1,LABEL2 // column per label
* -l LABEL // laber selector
* * -l 'LABEL!=VALUE' // not eq
* * -l LABEL in (VALUE1,VALUE2) // in
* * -l LABEL notin (VALUE1,VALUE2) // not in
* --namespace NAME // name space

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
  labels:
    creation_method: manual     # label
    env: prod                   # label
spec:
  nodeSelector:
    gpu: "true"                 # select node
  containers:
    - name: kubia               # container name
      image: kabanus/kubia      # image
      ports:
        - containerPort: 8080   # port
          protocol: TCP         # proto
      livenessProbe:            # Survivability check
        httpGet:                # Method: HTTP GET
          path: /               # HTTP request path
          port: 8080            # port
        initialDelaySeconds: 15 # First check delay
```

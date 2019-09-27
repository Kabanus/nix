##### print full 'kubeadm join'
> kubeadm token create --print-join-command

##### kubeadm join worker
> kubeadm join FQDN/IP:PORT --token TOKEN --discovery-token-ca-cert-hash HASH

##### kubeadm join master
> kubeadm join FQDN/IP:PORT --token TOKEN --discovery-token-ca-cert-hash HASH --control-plane

##### run image
> kubectl run APPNAME --image=REPO/NAME --port=8080 --generator=run/v1

##### create module
> kubectl create -f FILENAME.yaml

##### show module logs
> kubectl logs MODNAME -c CONTNAME

##### show previous logs
> kubectl logs PODNAME --previous

##### edit resource
> kubectl edit node|pod|rc|svc|ns NAME

##### expose service
> kubectl expose rc APPNAME --type=LoadBalancer --name NAME

##### port forwarding
> kubectl port-forward MODNAME LOCAL:MODULE

##### scale replication controller
> kubectl scale rc NAME --replicas=NUMBER

##### delete resources
> kubectl delete node|pod|rc|svc|ns NAME   
> kubectl delete pod -l creation_method=manual  
> kubectl delete rc NAME --cascade=false // don't delete pods   
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

##### exec command
> kubectl exec PODNAME -- CMD

##### exec shell
> kubectl exec -it PODNAME sh

###### JSONPath example
```
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'
```

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

###### Выражения для matchExpressions
* In – значение метки должно совпадать с одним из указанных значений values;
* NotIn – значение метки не должно совпадать с любым из указанных значений values;
* Exists – модуль должен содержать метку с указанным ключом (значение не важно). При использовании этого оператора не следует указывать поле values;
* DoesNotExist – модуль не должен содержать метку с указанным ключом. Свойство values не должно быть указано.

###### YAML example Pod
```
apiVersion: v1                  # API version
kind: Pod                       # module type
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
      livenessProbe:            # survivability check
        httpGet:                # method: HTTP GET
          path: /               # HTTP request path
          port: 8080            # port
        initialDelaySeconds: 15 # first check delay
```
###### YAML example Replication Controller
```
apiVersion: v1
kind: ReplicationController     # module type
metadata:
  name: kubia
spec:
  replicas: 3                   # replicas sum
  selector:
    app: kubia
  template:                     # new modules template
    metadata:
      labels:
        app: kubia
    spec:
      containers:
      - name: kubia
        image: luksa/kubia
        ports:
        - containerPort: 8080
```
###### YAML example Replica Set
```
apiVersion: apps/v1beta2
kind: ReplicaSet
metadata:
  name: kubia
spec:
  replicas: 3
  selector:
    matchLabels:
      app: kubia
  template:
    metadata:
      labels:
        app: kubia
    spec:
      containers:
      - name: kubia
        image: luksa/kubia
```
###### optional selector for Replica Set
```
  selector:
    matchExpressions:
      - key: app                # ключ
        operator: In            # выражение
        values:
          - kubia               # значение
```
###### YAML example Daemon Set
```
apiVersion: apps/v1beta2
kind: DaemonSet
metadata:
  name: ssd-monitor
spec:
  selector:
    matchLabels:
      app: ssd-monitor
  template:
    metadata:
      labels:
        app: ssd-monitor
    spec:
      nodeSelector:
        disk: ssd
      containers:
      - name: main
        image: luksa/ssd-monitor
```
###### YAML example Job
```
apiVersion: batch/v1
kind: Job
metadata:
  name: kubia-job
spec:
  completions: 5                # кол-во модулей
  parallelism: 2                # кол-во модулей выполняемых параллельно
  template:
    metadata:
      labels:
        app: batch-job
    spec:
      restartPolicy: OnFailure  # политика перезапуска
      activeDeadlineSeconds: 60 # ограничение работы модуля по времени
      containers:
      - name: main
        image: luksa/batch-job
```
###### YAML example CronJob
```
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: batch-job-every-fifteen-minutes
spec:
  schedule: "0,15,30,45 * * * *"  # min/hour/day/month/day of week
  jobTemplate:
    spec:
      template:
        metadata:
          labels:
            app: periodic-batch-job
        spec:
            restartPolicy: OnFailure
            containers:
            – name: main
              image: luksa/batch-job
```
###### YAML example Service
```
apiVersion: v1
kind: Service
metadata:
  name: kubia
spec:
  sessionAffinity: ClientIP   # bond client IP and pod
  ports:
  - name: http                # if multi-port - need name
    port: 80                  # service port
    targetPort: 8080          # container port
  - name: https               # if multi-port - need name
    port: 443                 # service port
    targetPort: 8443          # container port
  selector:
    app: kubia
```
###### YAML example Port Naming
```
kind: Pod
spec:
  containers:
  – name: kubia
    ports:
    – name: http
      containerPort: 8080     # name "http"
    – name: https
      containerPort: 8443     # name "https"
```
```
apiVersion: v1
kind: Service
spec:
  ports:
  – name: http
    port: 80
    targetPort: http          # name "http"
  – name: https
    port: 443
    targetPort: https         # name "https"
```
###### YAML exmaple External Service + Endpoints (no selector module)
```
apiVersion: v1
kind: Service
metadata:
  name: external-service  # Name (same in Endpoints)
spec:
  ports:
  – port: 80
```
```
apiVersion: v1
kind: Endpoints
metadata:
  name: external-service  # Name (same in Service)
subsets:
  – addresses:
    – ip: 11.11.11.11     # Endpoints
    – ip: 22.22.22.22     # Endpoints
    ports:
    – port: 80
```
```
apiVersion: v1
kind: Service
metadata:
  name: external-service
spec:
  type: ExternalName
  externalName: someapi.somecompany.com   # FQDN
  ports:
  – port: 80
```
###### YAML exampe NodePort
```
apiVersion: v1
kind: Service
metadata:
  name: kubia-nodeport
spec:
  type: NodePort        # Тип
  ports:
  - port: 80            # Порт внутреннего кластерного IP службы
    targetPort: 8080    # Целевой порт модулей, связанных с этой службой
    nodePort: 30123     # Порт узла кластера
  selector:
    app: kubia
```

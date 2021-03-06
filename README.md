Notes

```
# DOCS https://docs.gigaspaces.com/latest/admin/kubernetes-data-grid.html

$ helm install charts/xap-manager --name manager --namespace gigaspaces --set space.enabled=false
$ helm install charts/xap-pu --name pu --namespace gigaspaces --set manager.name=manager,partitions=1,ha=true
$ helm upgrade pu charts/xap-pu --namespace gigaspaces --set manager.name=manager,partitions=2,ha=true
```

Get all

```
$ kubectl get all -n gigaspaces -o wide
NAME                        READY     STATUS    RESTARTS   AGE       IP           NODE
pod/manager-xap-manager-0   1/1       Running   5          15m       172.17.0.6   minikube
pod/pu-xap-pu-1-0           1/1       Running   0          11m       172.17.0.7   minikube
pod/pu-xap-pu-1-1           1/1       Running   0          1m        172.17.0.8   minikube

NAME                                  TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)                               AGE       SELECTOR
service/manager-xap-manager-hs        ClusterIP   None          <none>        2181/TCP,2888/TCP,3888/TCP,4174/TCP   15m       selectorId=manager-xap-manager
service/manager-xap-manager-service   NodePort    10.105.63.9   <none>        8090:30890/TCP                        15m       selectorId=manager-xap-manager

NAME                                   DESIRED   CURRENT   AGE       CONTAINERS             IMAGES
statefulset.apps/manager-xap-manager   1         1         15m       gigaspaces-container   gigaspaces/xap-enterprise:14.2
statefulset.apps/pu-xap-pu-1           2         2         12m       pu-container           gigaspaces/xap-enterprise:14.2
```

Kubernetes dashboard

![Kubernetes dashboard](/screenshots/kubernetes-dashboard.png)

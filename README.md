Notes

```
# DOCS https://docs.gigaspaces.com/latest/admin/kubernetes-data-grid.html

$ helm install charts/xap-manager --name manager --namespace gigaspaces --set space.enabled=false
$ helm install charts/xap-pu --name pu --namespace gigaspaces --set manager.name=manager,partitions=1,ha=true
$ helm upgrade pu charts/xap-pu --namespace gigaspaces --set manager.name=manager,partitions=2,ha=true
```

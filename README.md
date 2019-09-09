Подготовка:
Кластер из двух нод, доступен через kubectl, все образы собраны.

gcloud container clusters get-credentials standard-cluster-3 --zone us-central1-a --project playground-248409
Сперва запускать, потом показывать


cd gcp-sql-creator-1
kubectl app

```
kubectl create -f deploy/service_account.yaml  
kubectl create -f deploy/role.yaml   
kubectl create -f deploy/role_binding.yaml 
```

```
kubectl create -f deploy/crds/workshops_v1_app_crd.yaml 
```

```
kubectl create -f deploy/operator.yaml
kubectl create -f deploy/crds/workshops_v1_app_cr.yaml
```
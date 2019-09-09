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


Finalizers are arbitrary string values, that when present ensure that a hard delete of a resource is not possible while they exist.

The first delete request on an object with finalizers sets a value for the metadata.deletionTimestamp field but does not delete it. Once this value is set, entries in the finalizer list can only be removed.

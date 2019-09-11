Пререквизиты:
k8s кластер, ключ сервис аккаунт в облаке gcp, установленный operator-sdk

Структура репозитория:
В какждой дирректории "gcp-sql-creator" находится набор файлов для сборки и деплоя оператора, для создания и удаления базы в GCP.

v1)   Нет действий при удалении базы

v1.1) задачи в роли по удалению базы описаны плохо, из-за этого не получается удалить CR и  CRD.(даже если убрать контроллер) Может быть полезно в данной ситуации https://github.com/kubernetes/kubernetes/issues/60538

v2) Корректно создает и удаляет базу.


Чтобы собрать оператор каждой версии необходимо:
1) Положить `key.json` (ключ от сервис аккаунта) в папки `gcp-sql-creator-1`, `gcp-sql-creator-1-1`, `gcp-sql-creator-2`
2) Выполнить `operator-sdk build <тэг>` из `gcp-sql-creator-1`, `gcp-sql-creator-1-1`, `gcp-sql-creator-2` для сборки докер образа.
3) Поменять в `gcp-sql-creator-1/deploy/operator.yaml` образ

```
cd gcp-sql-creator-1
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


Еще полезная ссылка про  finalizers: https://kubernetes.io/docs/tasks/access-kubernetes-api/custom-resources/custom-resource-definitions/#finalizers

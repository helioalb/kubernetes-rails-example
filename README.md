# Rails on kubernetes

## Add master key to kubernetes secrets

```shell
kubectl create secret generic rails-secrets --from-literal=rails_master_key='c8e77669b524379ca8c751e255265c1e'
```

:warning: Never versioning the rails_master_key. In this case it was made because it is an experiment.

##Configure postgres

```shell
kubectl apply -f config/kube/postgres
```

### Test postgres
```shell
kubectl --namespace=default port-forward svc/postgres 5432:5432 
```

```shell
psql --host 127.0.0.1 -U root -d kubernetes-rails-example_production -p 5432
```
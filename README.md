# k8s-gitlab

More info can be found in the [Gitlab documentation](https://docs.gitlab.com/charts/installation/deployment.html#deploy-using-helm)
```
helm repo add gitlab https://charts.gitlab.io/
helm repo update
export CHART_VERSION=$(helm search repo -r 'gitlab.*Git-repository' -o json | jq -r .[0].version)
helm upgrade -i gitlab gitlab/gitlab \
  --version ${CHART_VERSION} \
  --timeout 600s \
  -f values.yaml
```

## Additional info
The value file was saved using
```
export CHART_VERSION=$(helm search repo -o json | jq -r .[0].version)
helm show values gitlab/gitlab --version ${CHART_VERSION} > values.${CHART_VERSION}.yaml
```
and edited afterwards
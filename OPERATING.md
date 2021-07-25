# Operational / "imperative" cluster management

> Access cluster (locally with `kind`)

- see [kubernetes docs for accessing API server options](https://kubernetes.io/docs/tasks/administer-cluster/access-cluster-api/)

## Directly access the REST API with kubectl proxy

- [Reference](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#proxy)

> kubectl `proxy`, and curl that endpoint.
- `kubectl config view` to introspect config;

```
kubectl proxy --port=8080
```

```
curl 127.0.0.1:8080
```

- You'll get a list of endpoints. You can hit `/healthz`, `/api`, etc.

> You can run the process in the background (`&`) but you'll have to determine how you want to stop the process, preferably gracefully.

## CRD endpoints and verbs

- Note `group`, `version` and `domain` in `PROJECT` file for kubebuilder;
- Use the `group`, `version` and `domain` from `kubebuilder init` to curl endpoints after kubectl has been proxied:

```
curl 127.0.0.1:8080/apis/${GROUP}.${DOMAIN}/${VERSION}
```



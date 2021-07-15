# kubebuilder cronjob
https://book.kubebuilder.io/cronjob-tutorial/

## Kustomize /config
- Kustomize YAML defs for launching controller in cluster
- Kustomize base in `config/default`
- `config/manager`: Launch controllers as pods in cluster
- `/config/rbac`: permissions required to run controllers under svc acct

## controller runtime manager in main.go
- Runs all of our controllers and webhooks;
- Sets up clients to API server

## Kubernetes: Kinds, Resources
> Convention: resources are always the lowercase form of the Kind

- `Kind`: API type
- `Resource`: A usage of a `Kind` in the API
- Usually a 1:1 mapping between Kinds and resources, **but with CRDs, each Kind corresponds to a single resource**
- `Go`: GVK for GroupVersionKind
- `Go`: GVR for GroupVersionResource
- `Scheme`: tracking what Go type (GVR) corresponds to a GVK.

## API: Create Custom Resources and CRDs for our Kinds
> CRDs are a definition of our customized Objects, and the CRs are an instance of it.
- New APIs are how we teach Kubernetes about our custom objects;
- `Go structs` generate a `CRD`, which includes the data `schema`
- We then create instances of our custom objects;
- Those instances are managed by `controllers`. **Controllers manage the CR.**


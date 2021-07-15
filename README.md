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
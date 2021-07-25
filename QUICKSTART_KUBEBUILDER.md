# Kubebuilder quickstart

> Expected outcome: We'll see details in the PROJECT file which contain `domain`, `repo`, and `path` that we can use to operate on the cluster.

- [Init](#init)
- [Create API](#create-api)
- [Install CRDs into cluster](#install-crds-into-cluster)
- [Run the Controller](#run-the-controller)
- [Install instances of custom resources](#install-instances-of-custom-resources)
- [Run it on the cluster](#run-it-on-the-cluster)
- [Deploy the controller to the cluster with image](#deploy-the-controller-to-the-cluster-with-image)
- [Get the custom resource](#get-the-custom-resource)
- [Cleanup](#cleanup)

## Init

```sh
kubebuilder init --domain example.com --repo kubebuilder-cronjob
```

## Create API

> select yes for CR and Controller creation

```
kubebuilder create api --group webapp --version v1 --kind CronJob
```

## Install CRDs into cluster
```
make install
```

## Run the Controller
```
make run
```

## Install instances of custom resources

> In new tab:
```
kubectl apply -f config/samples/
```

## Run it on the cluster
Build and push your image to the location specified by `IMG`:

```
make docker-build docker-push IMG=<some-registry>/<project-name>:tag
```

## Deploy the controller to the cluster with image

```
make deploy IMG=<some-registry>/<project-name>:tag
```

## Get the custom resource
```
kubectl get guestbook
```

```
kubectl get guestbook -oyaml
```
- ... we could also add a shortname here and perform crud w kubectl api on that resource's shortname...
- ... we could add a label and select/delete/operate on, all custom resources which have that label ...

## Cleanup

### Uninstall CRDs
```
make uninstall
```

### Undeploy Controller
```
make undeploy
```
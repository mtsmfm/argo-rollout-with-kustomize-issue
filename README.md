# Argo rollout with kustomize issue

Deployment keeps `image: alpine` but Rollout doesn't.
Is this intentional?

```
$ kustomize version
{Version:3.6.1 GitCommit:c97fa946d576eb6ed559f17f2ac43b3b5a8d5dbd BuildDate:2020-05-27T23:39:00+01:00 GoOs:darwin GoArch:amd64}
```

```
$ kustomize build test-deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: test
spec:
  template:
    spec:
      containers:
      - image: alpine
        name: test
        resources:
          requests:
            memory: 1Mi
```

```
$ kustomize build test-rollout
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: test
spec:
  template:
    spec:
      containers:
      - name: test
        resources:
          requests:
            memory: 1Mi
```

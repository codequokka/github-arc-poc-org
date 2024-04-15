# Kind

## Deploy github ARC
```bash
❯ cd helm

❯ export .envrc

❯ helm version
version.BuildInfo{Version:"v3.14.4", GitCommit:"81c902a123462fd4052bc5e9aa9c513c4c8fc142", GitTreeState:"clean", GoVersion:"go1.21.9"}

❯ helmfile version

▓▓▓ helmfile

  Version            0.163.1
  Git Commit         8aa524c
  Build Date         25 Mar 24 23:48 UTC (2 weeks ago)
  Commit Date        25 Mar 24 23:45 UTC (2 weeks ago)
  Dirty Build        no
  Go version         1.22.1
  Compiler           gc
  Platform           linux/amd64

❯ kubectl create namespace arc-runners
namespace/arc-runners created

❯ kubectl -n arc-runners create secret generic pre-defined-secret --from-literal=github_token='<your-pat>'
secret/pre-defined-secret created

❯ helmfile diff -e $HELM_ENVIRONMENT

❯ helmfile apply -e $HELM_ENVIRONMENT
```

## Check github ARC is deployed
```bash
❯ kubectl get pods -n arc-systems
NAME                                             READY   STATUS    RESTARTS   AGE
arc-runner-set-754b578d-listener                 1/1     Running   0          3m24s
arc-systems-gha-rs-controller-547c844bc9-mb2fq   1/1     Running   0          34m
```

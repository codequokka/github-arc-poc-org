# Kind

## Deploy github ARC
```bash
❯ cd helm

❯ export .envrc

❯ helm version
version.BuildInfo{Version:"v3.14.4", GitCommit:"81c902a123462fd4052bc5e9aa9c513c4c8fc142", GitTreeState:"clean", GoVersion:"go1.21.9"}

❯ helm plugin install https://github.com/databus23/helm-diff
<omit>

❯ helm plugin install https://github.com/jkroepke/helm-secrets
<omit>

❯ helm plugin list
NAME    VERSION         DESCRIPTION
diff    3.9.5           Preview helm upgrade changes as a diff
secrets 4.6.1-dev       This plugin provides secrets values encryption for Helm charts secure storing

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

❯ age-keygen -o key.txt
Public key: <your-public-key>


❯ vi .sops.yaml
---
creation_rules:
  - age: <your-public-key>

❯ helm secrets encrypt -i github-arc/secrets-arc-runner-set-poc.yaml

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

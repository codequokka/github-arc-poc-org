# Kind

## Create K8s cluster
```bash
❯ kind create cluster --config=config.yaml
Creating cluster "github-arc-poc" ...
 ✓ Ensuring node image (kindest/node:v1.27.3) 🖼
 ✓ Preparing nodes 📦 📦 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
 ✓ Joining worker nodes 🚜
Set kubectl context to "kind-github-arc-poc"
You can now use your cluster with:

kubectl cluster-info --context kind-github-arc-poc

Thanks for using kind! 😊
```

## Check K8s nodes are ready
```bash
❯ kubectl get nodes
NAME                 STATUS   ROLES           AGE   VERSION
kind-control-plane   Ready    control-plane   69s   v1.27.3
kind-worker          Ready    <none>          31s   v1.27.3
kind-worker2         Ready    <none>          32s   v1.27.3
```

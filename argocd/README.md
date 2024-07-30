# .

```

helm repo add argo https://argoproj.github.io/argo-helm

helm install argocd argo/argo-cd -n devops -f ./argocd/values.yaml --version 6.7.15

# helm pull argo/argo-cd --untar --version 6.7.15


---
# git 의 helm 사용 시

cd argocd

helm install argocd ./argo-cd -n devops -f ./values.yaml
helm updrade argocd ./argo-cd -n devops -f ./values.yaml



```
# .

```

helm repo add gitea-charts https://dl.gitea.com/charts/

helm install gitea-server gitea-charts/gitea -n devops -f ./gitea/values.yaml --version 10.1.4

---
# git 의 helm 사용 시

cd gitea

helm install gitea-server ./gitea -n devops -f ./values.yaml
helm updrade gitea-server ./gitea -n devops -f ./values.yaml


```

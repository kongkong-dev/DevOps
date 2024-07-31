# .

```
### Valus.yaml 수정
#Befor
service.beta.kubernetes.io/ncloud-load-balancer-internal: "true" > 주석 적용

#After
annotaions: {} > 공백 적용



helm repo add argo https://argoproj.github.io/argo-helm

helm install argocd argo/argo-cd -n devops -f ./argocd/values.yaml --version 6.7.15

# helm pull argo/argo-cd --untar --version 6.7.15


---
# git 의 helm 사용 시

cd argocd

helm install argocd ./argo-cd -n devops -f ./values.yaml
helm updrade argocd ./argo-cd -n devops -f ./values.yaml



```

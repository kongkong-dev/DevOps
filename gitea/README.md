# .

```
##values.yaml 수정필요한 부분
#befor
  http:
    type: NodePort
    port: 3000

#After
  http:
    type: LoadBalancer
    port: 80


## 사전작업
1.. namespace   
> k create ns devops
2.. secret 추가
> kubectl create secret generic gitea-admin-sec --from-literal=username=hsj-devops --from-literal=password=P@ssword1! -n devops
3.. pvc 추가
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: gitea-shared-pvc
  namespace: devops
spec:
  storageClassName: nks-nas-csi
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 500Gi


helm repo add gitea-charts https://dl.gitea.com/charts/

helm install gitea-server gitea-charts/gitea -n devops -f ./gitea/values.yaml --version 10.1.4

---
# git 의 helm 사용 시

cd gitea

helm install gitea-server ./gitea -n devops -f ./values.yaml
helm updrade gitea-server ./gitea -n devops -f ./values.yaml


```

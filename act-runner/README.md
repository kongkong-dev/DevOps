# .

```

helm repo add vquie https://vquie.github.io/helm-charts

# helm pull vquie/act-runner --untar --version 1.0.0


helm install gitea-action -n devops vquie/act-runner -f ./act-runner/values.yaml --version 1.0.0

---
# git 의 helm 사용 시

cd act-runner

helm install gitea-action ./act-runner -n devops -f ./values.yaml
helm updrade gitea-action ./act-runner -n devops -f ./values.yaml




```

# runner docker iamge
gitea action의 빌드 속도를 높이기 위한 jdk 21 와 gradle8.7 을 포함한 image


```
docker build -t gitea-act-runner:jdk-21.0.2_v2 .
docker tag gitea-act-runner:jdk-21.0.2_v2 mia-registry.ncr.fin-ntruss.com/gitea-act-runner:jdk-21.0.2_v2
docker push mia-registry.ncr.fin-ntruss.com/gitea-act-runner:jdk-21.0.2_v2

```
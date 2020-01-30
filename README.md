# Purpose

ZCP Kubernetes dashboard는 ZCP와 연동하기 위한 Kubernetes dashboard입니다.

> IKS를 사용하게 되면 기본적으로 IBM Cloud와 통합된 Kubernetes dahsboard가 설치 됩니다. 해당 기능은 IBM 서비스에 종속적으로 동작합니다. 
> 
> 또한 IBM이 IKS 서비스를 위해 자동으로 관리하기 때문에 구성이나 설정이 변경되기 때문에 직접 관리할 수 있는 Dashboard를 설치 합니다. 
>
> 그래서 ZCP Addon과 연계할 수 있는 별도의 Kuberneters dashboard를 설치합니다. 차이가 있다면 Domain 설정시 SSL/TLS 제어를 Ingress를 이용합니다.  

# Installation

```
# tls 인증서 kube-system 으로 복사
$ kubectl patch secret cloudzcp-io-cert -n zcp-system -p='{"metadata": {"namespace": "kube-system"}}' --dry-run -o yaml | kubectl create -n kube-system -f -

# 새로운 kubernetes-dashboard 배포
$ kubectl create -f deployment.yaml -n kube-system
$ kubectl create -f service.yaml -n kube-system

# 도메인, ALB 설정 변경(확인)
$ kubectl create -f ingress.yaml -n kube-system
# AKS 인 경우
$ kubectl create -f ingress-aks.yaml -n kube-system
```

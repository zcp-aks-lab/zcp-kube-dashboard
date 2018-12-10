```
# tls 인증서 복사 
$ kubectl get secret cloudzcp-io-cert -o yaml -n zcp-system > cloudzcp-io-cert.yaml

# 파일 내부의 namespace 값을 kube-system 으로 수정
$ kubectl create -f cloudzcp-io-cert.yaml -n kube-system

# 새로운 kubernetes-dashboard 배포
$ kubectl create -f deployment.yaml -n kube-system
$ kubectl create -f service.yaml -n kube-system
$ kubectl create -f ingress.yaml -n kube-system
```

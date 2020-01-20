# Cert-Manager installation

- [Official Installation doc for K8s](https://cert-manager.io/docs/installation/kubernetes/)
- [Official Installation doc for OCP](https://cert-manager.io/docs/installation/openshift/)


- Cert-manager Installation
```
kubectl create namespace cert-manager
kubectl label namespace cert-manager certmanager.k8s.io/disable-validation=true
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.12.0/cert-manager.yaml
```

- How to check
```
kubectl get pods --namespace cert-manager
```

- Sample SelfSigned Issuer and Cert
```
cat <<EOF > test-resources.yaml
apiVersion: v1
kind: Namespace
metadata:
  name: cert-manager-test
---
apiVersion: cert-manager.io/v1alpha2
kind: Issuer
metadata:
  name: test-selfsigned
  namespace: cert-manager-test
spec:
  selfSigned: {}
---
apiVersion: cert-manager.io/v1alpha2
kind: Certificate
metadata:
  name: selfsigned-cert
  namespace: cert-manager-test
spec:
  commonName: example.com
  secretName: selfsigned-cert-tls
  issuerRef:
    name: test-selfsigned
EOF

kubectl create -f test-resources.yaml
kubectl describe certificate -n cert-manager-test
```

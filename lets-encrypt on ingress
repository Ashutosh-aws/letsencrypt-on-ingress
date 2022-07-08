# letsencrypt-on-ingress
## Configure cert manager for Nginx Ingress
kubectl command for Kubernetes version 1.16+

kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.1/cert-manager.yaml

## Kubernetes Nginx Ingress Controller LetsEncrypt
sudo nano  letsencrypt-issuer.yml

apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: letsencrypt-prod
  namespace: default
spec:
  acme:
    # The ACME server URL
    server: https://acme-v02.api.letsencrypt.org/directory
    # Email address used for ACME registration
    email: <EMAIL>
    # Name of a secret used to store the ACME account private key
    privateKeySecretRef:
      name: <NAME>
    # Enable the HTTP-01 challenge provider
    solvers:
    - http01:
        ingress:
          class: nginx
          
## Creating Nginx Ingress Let’s Encrypt TLS Certificate

apiVersion: cert-manager.io/v1
kind: Certificate
metadata:
  name: <NAME>
  namespace: <NAMEPSACE>
spec:
  secretName: <SECRET NAME>
  issuerRef:
    name: letsencrypt-prod
    kind: ClusterIssuer
  commonName: <DNS>
  dnsNames:
  - <DNS>
  
CHECK THE SECRET WITH ABOVE SECRETNAME & CERTICATE
  
## Point Nginx Ingress Let’s Encrypt Certificate in Nginx Ingress
  
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt-prod
  
  tls:
  - hosts:
    - <DNS>
    secretName: <SECRET NAME>
  

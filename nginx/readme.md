## Deploy Nginx

### Apply the deployment

```bash
kubectl apply -f deployment.yaml
```

### Apply Ingress without TLS

```bash
kubectl apply -f ingress.yaml
```

### How to get the TLS secret local deployment (self-signed)

Create the private key

```bash
openssl genpkey -algorithm RSA -out private-key.pem
```

Create the Self-Signed Certificate

```bash
openssl req -new -x509 -key private-key.pem -out certificate.crt
```

### Register the TLS secret

```bash
kubectl create secret tls nginx-tsl --cert=./certificate.crt --key=./private-key.pem
```

### Apply Ingress with TLS

```bash
kubectl apply -f ingress-tls.yaml
```

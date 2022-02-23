# Traefik Keycloak

```powershell
Copy-Item $env:LOCALAPPDATA/mkcert/rootCA.pem ./data/certs/cacerts.crt
Copy-Item $env:LOCALAPPDATA/mkcert/rootCA-key.pem ./data/certs/cacerts.key

cd ./data/certs
mkcert k8s.local '*.k8s.local' localhost 127.0.0.1 ::1
```

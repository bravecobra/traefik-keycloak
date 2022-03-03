# Traefik Keycloak

## Create self-signed certificates

```powershell
Copy-Item $env:LOCALAPPDATA/mkcert/rootCA.pem ./data/certs/cacerts.crt
Copy-Item $env:LOCALAPPDATA/mkcert/rootCA-key.pem ./data/certs/cacerts.key

cd ./data/certs
mkcert k8s.local '*.k8s.local' localhost 127.0.0.1 ::1
```

## Start environment

```powershell
docker-compose up -d
```

## Configure keycloak

### Create a client

Create a realm `k8s.local` to operate in.
![Create realm](images/keycloak-realm.png "k8s.local realm")

Then create a client for `traefik-forward-auth` in that realm

![Create traefik-forward-auth client](images/keycloak-client.png "traefik-forward-auth client")

Capture the Client Secret, store it in the `.env` file and re-apply the docker-compose config.

Also create a user to login with.

## TODO

- [ ] Switch to mesosphere/traefik-forward-auth?

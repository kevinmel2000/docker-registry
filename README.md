# Private Docker Registry
Private Docker Registry with Nginx and Basic Authentication

# Howto

```
git clone https://github.com/ndlrx/docker-registry
```

Add SSL Certificates to nginx/conf.d/ssl/

```
cp /path/to/ssl/fullchain.pem nginx/conf.d/ssl/
cp /path/to/ssl/privkey.pem nginx/conf.d/ssl/
```

Add Root CA to Docker and System

```
mkdir -p /etc/docker/certs.d/registry.hakase-labs.io/
cp rootCA.crt /etc/docker/certs.d/registry.hakase-labs.io/

mkdir -p /usr/share/ca-certificates/extra/
cp rootCA.crt /usr/share/ca-certificates/extra/
```

Update ca-certificates and Restart Docker Service.

```
sudo dpkg-reconfigure ca-certificates
systemctl restart docker
```

Test

```
docker login https://registry.hakase-labs.io/v2/
http -a hakase https://registry.hakase-labs.io/v2/_catalog
```

Results:



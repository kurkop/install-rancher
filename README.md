# install-rancher
Rancher with local nginx and certs SSL. Basic configuration

## Create certs with let's encrypt

Exists a image for create interactively the ssl certs. Only is necessary run the next command:

```
sudo docker run -it --rm -p 443:443 -p 80:80 --name certbot -v "/etc/letsencrypt:/etc/letsencrypt" -v "/var/lib/letsencrypt:/var/lib/letsencrypt" quay.io/letsencrypt/letsencrypt:latest certonly
```

And run as webserver and define a subdomain: "mydomain.co" (for this example).

## Install nginx in local server

* Install with apt or yum (apt-get install -y nginx)
* Add rancher.conf to /etc/nginx/config.d or /etc/nginx/sites-enable (In redhat or debian distros)
* Restart service
 
## Run rancher
```
sudo docker run -d -v rancher-data:/var/lib/mysql --restart=always -p 8080:8080 rancher/server
```

#### This is all.

# auto ssl and proxy server
## have to use docker or docker compose only

## Proxy
start with proxy server, I use jwilder/nginx-proxy image for make proxy.
### How it works
- first add env name VIRTUAL_HOST=your_domain.com to container you want to proxy
- mount "/var/run/docker.sock:/tmp/docker.sock:ro" to jwilder/nginx-proxy container
### Usage
curl -H "Host: your_domain.com" localhost

## Auto SSL
when we got proxy server, so now we'll add jrcs/letsencrypt-nginx-proxy-companion to make our ssl
### How it works
- after we setup proxy server, Now we have to add 3 new things for both proxy and letencrypt container.
- "your_path:/usr/share/nginx/html" to write http-01 challenge files.
- "your_path2:/etc/nginx/certs" to store certificates, private keys and ACME account keys (readonly for the nginx-proxy container).
- "your_path3:/etc/nginx/vhost.d" to change the configuration of vhosts (required so the CA may access http-01 challenge files).
- Now for create ssl to your domain you just add 2 env to your container
- LETSENCRYPT_HOST=your_domain.com should be the same as VIRTUAL_HOST
- LETSENCRYPT_EMAIL=your@email.com
### Usage
curl -H "Host: your_domain.com" https://localhost
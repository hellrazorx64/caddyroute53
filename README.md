# This configuration is using the latest version of the AWS module which seems to be incompatible. Will update as soon the problem is fixed.
First commit should still work but is not up to date

# Caddy Route53 DNS Challenge
Caddy Docker Image With custom build for route53 using Docker-Compose

This is a simple project that uses a custom caddy build in order to allow DNS challenge method to generate a valid tls for AWS Route 53 for a server that is not public facing.

> Note: You can potentially use this whole method and open up the destination to the web and close it when it is no longer needed.

## Prequisites
- docker-compose
- caddyaws.zip

## Get the files
> Extract the caddyaws.zip archive, the following files are included:

- docker-compose.yml
- caddyaws
- Caddyfile
- .env

## Configuration
### .env file
> the purpose of this file is to hide your precious API keys off the raw configuration files

aws_profile= user you created on aws for dns api access

access_key_id= generated api key

secret_access_key= generated secret

### docker-compose file

- DOMAIN=your.domain.com
- EMAIL=Email to be used for certs renewal notice

### Caddyfile

simply change the *IP#OR#HOSTNAME:PORT* to the server this hostname should redirect to

Example: reverse_proxy 192.168.10.1:8006
or
reverse_proxy nameofserver.internaladdress.home:8006

### Run it

```shell
docker-compose up -d
```


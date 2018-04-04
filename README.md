# Localtunnel NGINX docker server setup

This is a basic localtunnel NGINX setup using docker-compose

## Installation

### Environment vars
Copy the `.env.dist` for to `.env` and modify the parameters defined in the file.

`LOCALTUNNEL_DOMAIN`: The domain the localtunnel is running on. Eg: `tunnel.example.com`

### Domain
You'll need to set up `tunnel.example.com` and `*.tunnel.example.com` in your DNS control panel to resolve to the IP the containers are running on.

### Certificate
Next, you'll need to generate your certificates in the `ssl` folder, this folder will be mounted in the container and used by NGINX.

In the root of this folder, run:
```shell
mkdir ./ssl
openssl req -x509 -nodes -days 5000 -newkey rsa:2048 -keyout ./ssl/server.key -out ./ssl/server.crt
```
Just follow the instructions, fill in the information as desired.

### Startup

Finally, you start the server by running `docker-compose up -d`

## Usage

Once started, you can simply use localtunnel with the `--host` parameter:
```
lt -p 80 --host http://tunnel.example.com
``` 

More info can be found at https://github.com/localtunnel/localtunnel


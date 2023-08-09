# SearxNG & NGINX

SearxNG using an external NGINX container through `net-searxng` external network.

You can use [certginx](https://github.com/heartnerds/certginx) to manage NGINX.

## **Docker Configuration**

Create the external network
```sh
docker network create net-searxng
```

## **Filtron Configuration**

Import the rules from searxng
```sh
curl https://raw.githubusercontent.com/searxng/searxng-docker/master/rules.json > rules.json
```

## **SearxNG Configuration**

Update the `.env` file.

Replace key in .env
```sh
sed -i "s|ReplaceWithARealKey|$(openssl rand -base64 33)|g" .env
```

Generate settings.yml 
```sh
docker compose up -d && docker compose down
```


## **NGINX Configuration**

Replace the template domain with your real domain *(Change `my_domain.example` with your real domain name)*
```sh
sed -i "s/change_me.example/my_domain.example/g" nginx.conf
```

If your are using [certginx](https://github.com/heartnerds/certginx), move `nginx.conf` to your certginx instance in `./nginx/conf.d/<your-domain>.conf`

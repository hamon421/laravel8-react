# Laravel9 + Next.js
## docker起動
```shell
docker-compose up -d
docker-compose down
```

## 構成

### front

### api
- image: php:8.1-fpm
- TCP Socket: api:9000
### nginx
- image: nginx:1.21
### db
- image: mysql:8.0
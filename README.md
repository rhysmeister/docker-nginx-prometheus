# docker-nginx-lua-prometheus

# Build & run docker container

```bash
docker build --rm --tag centos7-nginx .
docker run -p 80:80 -p 4040:4040 -tid --rm --privileged centos7-nginx
```

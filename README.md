# docker-nginx-prometheus

# Build & run docker container

```bash
docker build --rm --tag centos7-nginx .
docker run -p 80:80 -p 4040:4040 -tid --rm --privileged centos7-nginx
```
# Check systemd services in docker container

```bash
systemctl status nginx
systemctl status prometheus-nginxlog-exporter
```

* Nginx & Prometheus endpoints

* nginx - http://localhost:80
* Prometheus endpoint - http://localhost:4040/metrics

# Prometheus endpoint data

```
# HELP nginx_http_response_count_total Amount of processed HTTP requests
# TYPE nginx_http_response_count_total counter
nginx_http_response_count_total{app="default",method="GET",status="304"} 11
nginx_http_response_count_total{app="default",method="GET",status="404"} 13
# HELP nginx_http_response_size_bytes Total amount of transferred bytes
# TYPE nginx_http_response_size_bytes counter
nginx_http_response_size_bytes{app="default",method="GET",status="304"} 0
nginx_http_response_size_bytes{app="default",method="GET",status="404"} 1989
# HELP nginx_parse_errors_total Total number of log file lines that could not be parsed
# TYPE nginx_parse_errors_total counter
nginx_parse_errors_total 0
```
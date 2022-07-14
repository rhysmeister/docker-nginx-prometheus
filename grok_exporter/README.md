# grok_exporter

A quick PoC of [grok_exporter](https://github.com/fstab/grok_exporter)


# Build & run docker container

```bash
docker build --tag centos7-grok .
docker run -p 80:80 -p 9144:9144 -tid --rm --privileged centos7-grok
```

# Check systemd services in docker container

```bash
systemctl status nginx
systemctl status grok_exporter
```

Check logs for grok_exporter service...

```bash
journalctl -u grok_exporter
```

# Nginx & Prometheus endpoints

* [nginx](http://localhost/)
* [Grok Exporter Endpoint](http://localhost/)


# Prometheus endpoint data

# Sample /var/log/nginx/access.log

```
12/Jul/2022:10:22:35 +0000 msec="1657621355.602" src_ip="172.17.0.1:60092" requested_host="localhost" requested_method="GET" requested_url="/" HTTP/1.1 http_response="304" http_referral="-" useragent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:102.0) Gecko/20100101 Firefox/102.0" http_cookies="-" lmx_cookie="false" wrong_bookmark="false" persistence="-" requested_length="547" bytes_sent="0" requests_per_connection="5" upstream_response_time="-" request_time="0.000"
12/Jul/2022:10:22:35 +0000 msec="1657621355.690" src_ip="172.17.0.1:60092" requested_host="localhost" requested_method="GET" requested_url="/" HTTP/1.1 http_response="304" http_referral="-" useragent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:102.0) Gecko/20100101 Firefox/102.0" http_cookies="-" lmx_cookie="false" wrong_bookmark="false" persistence="-" requested_length="547" bytes_sent="0" requests_per_connection="6" upstream_response_time="-" request_time="0.000"
12/Jul/2022:11:02:59 +0000 msec="1657623779.102" src_ip="172.17.0.1:60096" requested_host="localhost" requested_method="GET" requested_url="/idonotexist" HTTP/1.1 http_response="404" http_referral="-" useragent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:102.0) Gecko/20100101 Firefox/102.0" http_cookies="-" lmx_cookie="false" wrong_bookmark="false" persistence="-" requested_length="477" bytes_sent="153" requests_per_connection="1" upstream_response_time="-" request_time="0.000"
```

# Additional Resources

The following resources might be useful should we proceed with grok_exporter

* https://github.com/eRadical/ansible-grok-exporter
# https://github.com/fstab/grok_exporter/blob/master/CONFIG.md
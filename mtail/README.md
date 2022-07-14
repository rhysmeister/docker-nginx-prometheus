# Google mtail

# Links

* [mtail github](https://github.com/google/mtail)

# Build & run docker container

```bash
docker build --tag centos7-mtail .
docker run -p 80:80 -p 3903:3903 -tid --rm --privileged centos7-mtail
```

# Check systemd services in docker container


```bash
systemctl status nginx
systemctl status mtail
```

# Nginx & Prometheus endpoints

* [nginx](http://localhost/)
* [Mtail Status/Info Endpoint](http://localhost:3903/)
* [Mtail Prometheus Endpoint](http://localhost:3903/metrics)

# Testing mtail programs

* Syntax check

```bash
/opt/mtail/mtail --compile_only --progs /etc/mtail/
```

* Dry run

```bash
/opt/mtail/mtail --one_shot --progs /etc/mtail --logs /var/log/nginx/access.log
```

# Links

* [mtail systemd example](https://stackoverflow.com/questions/57842778/how-to-configure-mtail-with-nginx-and-prometheus)
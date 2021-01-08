# 查看数据卷目录



* 查看数据卷目录

  ```text
  ❯ docker ps
  CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                              NAMES
  4921388fd12e        prom/prometheus     "/bin/prometheus --c…"   25 minutes ago      Up 24 minutes       9090/tcp                                                           root_prometheus_1
  7af8aa4ae2e8        traefik:latest      "/entrypoint.sh --ap…"   21 hours ago        Up 21 hours         0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp, 0.0.0.0:8080->8080/tcp   root_traefik_1
  1ecf1c53559d        grafana/grafana     "/run.sh"                23 hours ago        Up 22 hours         3000/tcp                                                           root_grafana_1
  ❯ docker inspect --format "{{.Config.Volumes}}" 4921388fd12e
  map[/etc/prometheus/prometheus.yml:{} /prometheus:{}]
  ❯ docker inspect -f "{{.Mounts}}" 4921388fd12e
  [{bind  /root/prometheus.yml /etc/prometheus/prometheus.yml  rw true rprivate} {volume f9f579cb9ca6ac88d3bf8e10d0ca263646e00b77414c37952c4ea61dc16b277e /var/lib/docker/volumes/f9f579cb9ca6ac88d3bf8e10d0ca263646e00b77414c37952c4ea61dc16b277e/_data /prometheus local rw true }]
  ```

  ```text
  CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                              NAMES
  4921388fd12e        prom/prometheus     "/bin/prometheus --c…"   31 minutes ago      Up 31 minutes       9090/tcp                                                           root_prometheus_1
  ❯ docker inspect 4921388fd12e|grep Mounts -A 20
          "Mounts": [
              {
                  "Type": "bind",
                  "Source": "/root/prometheus.yml",
                  "Destination": "/etc/prometheus/prometheus.yml",
                  "Mode": "rw",
                  "RW": true,
                  "Propagation": "rprivate"
              },
              {
                  "Type": "volume",
                  "Name": "f9f579cb9ca6ac88d3bf8e10d0ca263646e00b77414c37952c4ea61dc16b277e",
                  "Source": "/var/lib/docker/volumes/f9f579cb9ca6ac88d3bf8e10d0ca263646e00b77414c37952c4ea61dc16b277e/_data",
                  "Destination": "/prometheus",
                  "Driver": "local",
                  "Mode": "rw",
                  "RW": true,
                  "Propagation": ""
              }
          ],
          "Config": {
  ```

![](../.gitbook/assets/image%20%281%29.png)


# traefik-docker-demo
Demo docker-compose stack for Traefik, Docker, Nginx, and whoami Container

## Step by step

### 設定 `/etc/hosts` 模擬 DNS

```
# etc/hosts
127.0.0.1       localhost monitor.local.com web.local.com web2.local.com whoami.local.com
```

### 建立 Traefik 使用的 Docker Network Interface

```bash
$ docker network create traefik-web
```

### 啟動 Traefik

```bash
$ cd traefik
$ ./up.sh
```

此時瀏覽 `http://monitor.local.com/dashboard/` 或是 `http://localhost:8080/dashboard` 查看 Traefik Dashboard

### 啟動 Nginx 與 `whoami` Container

```bash
$ cd web
$ ./up.sh
```

接著可以瀏覽：

* `web.local.com`
* `web2.local.com`
* `whoami.local.com`
* `whoami.local.com/whoami`

查看所有 Container 是否正常運作。

[`whoami` Container](https://github.com/containous/whoami) 也還有其他的 Endpoint，有些可以運作正常，有些看似無法正常運作，參考 Source Code 以後發現有以下 Endpoint：

* `/`
* `/data`
* `/echo`
* `/bench`
* `/api`
* `/health`

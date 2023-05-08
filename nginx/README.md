## ghcr.io/rayriffy/nginx

Non-root version of nginx with [`distroless/base` image](https://github.com/GoogleContainerTools/distroless/blob/main/base/README.md)

Usage
---

```
docker run --name instance -p 80:80 ghcr.io/rayriffy/nginx
```

Running unprivileged version of nginx with existing configuration may results in a crash. I reccomend to copy base config from the image itself first then adjust to your system.

```
docker create --name instance ghcr.io/rayriffy/nginx
docker cp instance:/etc/nginx/nginx.conf ./
docker rm instance
```

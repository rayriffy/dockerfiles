## ghcr.io/rayriffy/hentaiathome

H@H client with distroless to running an instance minus the operating system.

Usage
---

Push secret token to directory

```
mkdir -p ./data/data
echo -n "<H@H Key>" > ./data/data/client_login
```

Create `docker-compose` template and adjust settings accordingly

```yml
version: "3.9"
services:
  #
  # Hentai@Home
  #
  hentaiathome:
    container_name: hentaiathome
    restart: unless-stopped
    ports:
      - "43654:43654"
    volumes:
      - ./data:/hath/data
      - ./download:/hath/download
    image: ghcr.io/rayriffy/hentaiathome:latest

```

# Media Stack

Self-hosted media server powered by Docker Compose.

## Services

- **Jellyfin** – media server
- **Sonarr** – TV automation
- **Radarr** – movie automation
- **Bazarr** – subtitles
- **Prowlarr** – indexer manager
- **qBittorrent** – downloader
- **Seerr** – request management
- **Flaresolverr** – Cloudflare bypass for indexers

---

## Requirements

- Docker
- Docker Compose
- External Docker network:

```bash
docker network create media_net
````

---

## Directory Structure

Expected layout on host:

```
/home/patrick/mediaserver/
├── config/
├── downloads/
└── media/
    ├── movies/
    └── tv/
```

---

## Usage

Start the stack:

```bash
docker compose up -d
```

Stop:

```bash
docker compose down
```

---

## Ports

| Service      | Port |
| ------------ | ---- |
| Jellyfin     | 8096 |
| Seerr        | 5055 |
| qBittorrent  | 8080 |
| Sonarr       | 8989 |
| Radarr       | 7878 |
| Bazarr       | 6767 |
| Prowlarr     | 9696 |
| Flaresolverr | 8191 |

---

## Notes

* All services run on a shared `media_net` network
* Media is mounted read-only in Jellyfin
* Downloads are shared between qBittorrent and *arr apps
* Uses UID/GID `1000` for permissions

---

## TODO (optional improvements)

* Replace hardcoded paths with `.env`
* Add reverse proxy (Caddy / Traefik)
* Add authentication layer (Authelia)
* Add backups for config volumes
* Add monitoring (Prometheus + Grafana)

---

## Disclaimer

This project is for personal use. Make sure you comply with your local laws and content policies.

```

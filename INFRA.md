# 🏗️ Infrastructure Overview

## Repository Purpose

This repo defines the Purrbrews homelab infrastructure using Docker Compose.
It provides a modular service architecture for Home Assistant, Immich, and Vaultwarden with shared environment configuration.

## Architecture Summary

- `homeassistant/` — Home Assistant container with host networking and hardware passthrough for Zigbee/Z-Wave/Bluetooth.
- `immich/` — Self-hosted photo management platform with Redis, Postgres, and machine learning services.
- `vaultwarden/` — Lightweight password manager with SMTP integration and hardened login controls.
- `env` — Shared environment variable definitions used across services.

## Environment Management

The repository uses a centralized `env` file for shared configuration values:

- `DOMAIN`
- `TZ`
- `PROJECT_NAME`
- `PROJECT_DIR`
- `DATA_DIR`
- `MEDIA_DIR`
- `EMAIL_USERNAME`, `EMAIL_PASSWORD`, `SMTP_HOST`, `SMTP_PORT`
- `IMAP_HOST`, `IMAP_PORT`

Each service also loads its own local `.env` file when required.

## Service Details

### Home Assistant

- Image: `ghcr.io/home-assistant/home-assistant:stable`
- Container name: `homeassistant`
- Restart policy: `unless-stopped`
- `privileged: true` and `network_mode: host` for direct hardware access.
- Volumes:
  - `${DATA_DIR}/homeassistant:/config`
  - `/etc/localtime:/etc/localtime:ro`
  - `/run/dbus:/run/dbus:ro`
  - `/dev:/dev`
- Healthcheck: `curl -f http://localhost:8123`

### Immich

- Services:
  - `immich-server`
  - `immich-machine-learning`
  - `redis`
  - `database`
- `immich-server` uses `${IMMICH_PORT}:3001` and stores uploads at `${MEDIA_DIR}/immich`.
- Machine learning service caches models at `${DATA_DIR}/immich/model-cache`.
- Redis provides session caching and queueing.
- Postgres is tuned for NVMe with custom command options.
- Hardware passthrough: `/dev/dri` for Intel QuickSync acceleration.

### Vaultwarden

- Image: `vaultwarden/server:latest`
- Container name: `vaultwarden`
- Restart policy: `unless-stopped`
- Environment-driven domain and SMTP settings.
- Volume: `${DATA_DIR}/vaultwarden:/data`
- Port mapping: `8080:80`
- Secure defaults:
  - `SIGNUPS_ALLOWED=false`
  - `INVITATIONS_ALLOWED=true`
  - `SHOW_PASSWORD_HINT=false`
  - Rate limiting enabled
- Healthcheck: `curl -f http://localhost:80/health`

## Data Location Strategy

The expected directory variables are:

- `PROJECT_DIR` — root path of this repository deployment
- `DATA_DIR` — service state and config
- `MEDIA_DIR` — media uploads and asset storage

This separation keeps persistent data outside container lifetimes and improves upgrade safety.

## Security Considerations

- Do not commit secrets or real credentials to the repository.
- Keep `env` and any generated `.env` files private.
- Use a reverse proxy and TLS when exposing services externally.
- Prefer internal network access for Home Assistant and Vaultwarden.

## Notes

This infrastructure is designed for a self-hosted homelab environment with modern container patterns and hardware acceleration.
For installation instructions, see `INSTALLATION_GUIDES.md`.

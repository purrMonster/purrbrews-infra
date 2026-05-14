# 🛠️ Installation Guides

## Prerequisites

- Docker Engine
- Docker Compose v2 or later
- Linux/macOS host with access to required devices
- A working `env` file configured at the repository root
- Optional: reverse proxy and TLS if exposing services externally

## 1. Configure Shared Environment

Copy the root `env` file into a secure file or edit it directly.

Required values:

- `DOMAIN` — your homelab domain
- `TZ` — timezone
- `PROJECT_NAME`
- `PROJECT_DIR`
- `DATA_DIR`
- `MEDIA_DIR`
- `EMAIL_USERNAME`, `EMAIL_PASSWORD`
- `SMTP_HOST`, `SMTP_PORT`
- `IMAP_HOST`, `IMAP_PORT`

Example:

```bash
DOMAIN="yourdomain.example.com"
TZ="Asia/Kolkata"
PROJECT_NAME="purrbrews"
PROJECT_DIR="/opt/purrbrews-infra"
DATA_DIR="/storage/data"
MEDIA_DIR="/storage/media"
EMAIL_USERNAME="vault@example.com"
EMAIL_PASSWORD="supersecret"
SMTP_HOST="smtp.example.com"
SMTP_PORT=587
IMAP_HOST="imap.example.com"
IMAP_PORT=993
```

## 2. Deploy Home Assistant

1. Change into the service directory:

```bash
cd homeassistant
```

2. Start the stack:

```bash
docker compose up -d
```

3. Verify via `http://<host>:8123`

## 3. Deploy Immich

1. Change into the service directory:

```bash
cd immich
```

2. Start the stack:

```bash
docker compose up -d
```

3. Verify via `http://<host>:${IMMICH_PORT}`

## 4. Deploy Vaultwarden

1. Change into the service directory:

```bash
cd vaultwarden
```

2. Create or confirm `ADMIN_TOKEN` in `vaultwarden/env`.

3. Start Vaultwarden:

```bash
docker compose up -d
```

4. Verify via `http://<host>:8080`

## 5. Common Commands

- Start a service:

```bash
docker compose up -d
```

- Stop a service:

```bash
docker compose down
```

- Inspect logs:

```bash
docker compose logs --follow
```

- Validate compose configuration:

```bash
docker compose config
```

## 6. Upgrade Notes

- Stop the service before updating if needed.
- Pull the latest images:

```bash
docker compose pull
```

- Restart the stack:

```bash
docker compose up -d
```

- Confirm the service is healthy after restart.

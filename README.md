# 🐾 purrbrewws-infra
> High-performance homelab infrastructure for the Purrbrews stack.
NOTE: ALL DOCUMENTATIONS ARE AI GENERATED.
---

## 📊 System Status

| Component | Status |
| --- | --- |
| Maintenance | 🟢 Active / In progress |
| Current Run Status | 🟢 RUNNING |
| Last Updated | `2026-05-24` |
| Total Services | `7` stacks + support directories |
| Healthchecks | ✅ Home Assistant, Immich, Vaultwarden, Nextcloud, Paperless-NGX |

---

## 🛠️ Repository Overview

### Included stacks

- `arr-stack/` — app stack utilities
- `authelia/` — authentication and SSO gateway with Redis and Postgres
- `homeassistant/` — automation platform with hardware passthrough
- `immich/` — photo library, ML processing, Redis, Postgres
- `nextcloud/` — file sync and collaboration
- `vaultwarden/` — password management with SMTP
- `vikunja/` — task and project management
- `paperless-ngx/` — document scanning and OCR
- `env` — centralized environment configuration

### Service icons

- 🏠 Home Assistant
- 📸 Immich
- 🔐 Vaultwarden
- 📦 Nextcloud
- ✅ Vikunja
- 🔐 Authelia

---

## 📚 Documentation References

- `INFRA.md` — design, architecture, and infrastructure details
- `INSTALLATION_GUIDES.md` — deployment, setup, and install workflow
- `DAILY_LOG.md` — daily notes, changelog, and commit history

---

## 🚀 Runtime Metrics

- `Docker Compose` stacks: `homeassistant`, `immich`, `vaultwarden`
- `Docker Compose` stacks: `homeassistant`, `immich`, `vaultwarden`, `nextcloud`, `paperless-ngx`
- `Env` sources: `env` (shared) + service-local env families
- `Persistent storage`: `${DATA_DIR}`, `${MEDIA_DIR}`
- `Hardware passthrough`: `/dev`, `/run/dbus`, `/dev/dri`
- `Security`: admin tokens, SMTP auth, rate limiting, no open signups

---

## 🔧 Summary

This repo is built for reliable, scalable homelab operations. It blends secure self-hosting with optimized performance for media and automation workloads.

### Key focus areas

- `Home Assistant` for automation and device integration
- `Immich` for local image storage and machine learning
- `Vaultwarden` for secure password management

---

## ⚠️ Notes

- Keep secrets out of version control.
- Use internal DNS or a reverse proxy for service exposure.
- Confirm `env` variable paths and ports before launch.
- Open documentation pages for detailed service and installation guidance.


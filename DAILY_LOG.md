# 📅 DAILY LOG

**Documentation generated as of commit `c347faa`**

---

## 2026-06-04

- Linux voice assistant (LVA) service removal (commit `c347faa`):
  - Removed `linux-voice-assistant/` service from the stack.
  - Service was experimental and deemed not essential for the current infrastructure.
- Documentation updates for consistency:
  - Updated directory references from `authelia/` to `authelio/` across all markdown files.
  - Updated `INFRA.md`, `INSTALLATION_GUIDES.md`, `README.md`, and `DAILY_LOG.md` for accuracy.
  - Current service count: 7 stacks (`authelio`, `homeassistant`, `immich`, `nextcloud`, `paperless-ngx`, `vaultwarden`, `vikunja`).
- Last update date bumped to `2026-06-04` in system status documentation.

## 2026-05-25

- Linux voice assistant (LVA) service added (commit `1486450`):
  - New service addition: `linux-voice-assistant/` with full Docker Compose orchestration.
  - Included local environment configuration for service-specific settings.
  - Initial experimental support for voice assistant integration within the homelab stack.

## 2026-05-24

- Documentation update (commit `c24f2be`):
  - Comprehensive updates to `DAILY_LOG.md`, `INFRA.md`, `INSTALLATION_GUIDES.md`, and `README.md`.
  - Fixed markdown formatting and layout inconsistencies.
  - Added detailed service deployment guides and architecture documentation.
- Authelia service (`authelio/`) implementation and standardization (commit `558f77f`):
  - Added `version: "3.9"` specification.
  - Implemented `env_file` loading from `../env` and local `.env` for centralized and service-specific secrets.
  - Added healthchecks with authenticated Redis ping and Postgres readiness verification.
  - Restructured environment variables for clarity (`AUTHELIA_POSTGRES_USER`, `AUTHELIA_REDIS_PASSWORD`, `AUTHELIA_STORAGE_POSTGRES_PASSWORD`).
  - Created `.env` template with secure secret placeholders.
- Network configuration improvements (commit `f83a510`):
  - Removed proxy network requirements from authelia compose, allowing standalone deployments.
- Repository: Created root-level `.env` file aligned with sibling service env patterns.
- Code verification completed: identified and documented env file naming inconsistencies across services for future standardization.

## 2026-05-23

- Vikunja service added and stabilized:
  - Initial vikunja support with Postgres and Redis backend (commit `db7c585`).
  - VIKUNJA configuration fixes for database connectivity (commit `fe0a017`).
  - User and database configuration refinements (commits `bfd54ba`, `085b02f`).
- Documentation updated to include full vikunja service details, deployment steps, and environment configuration.

## 2026-05-22

- Changed system port configuration and related compose/network adjustments.

## 2026-05-21

- `paperless-ngx` — updated environment configuration and added SMTP/email support.
- `nextcloud` — added Redis cache and SMTP support.
- Repository: linting and code-style adjustments.

## 2026-05-15

- `immich` service added with full Docker Compose orchestration.
- Root environment handling standardized from `.env` to `env`.
- `homeassistant` compose configuration updated to use shared environment and verify host device access.
- `vaultwarden` environment integration improved with SMTP settings and security hardening.
- Multiple Vaultwarden compose adjustments made to remove redundancy and enforce correct env file structure.

## 2026-05-14

- Standardized `env` handling across services.
- `homeassistant` — initial compose/config additions.
- `vaultwarden` — compose and env integration improvements.
- Misc: typo fixes, removed redundant compose code, committed environment paths, and project bootstrap.

## Notes

- Keep this file updated with deployment and configuration changes.
- Document any service upgrades, environment layout changes, or network topology revisions here.

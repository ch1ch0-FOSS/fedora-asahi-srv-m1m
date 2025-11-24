# asahi-srv-infrastructure

ARM64 server infrastructure on Asahi Linux (Fedora Asahi Remix).

## Overview

Infrastructure-as-code for Mac Mini M1 running Fedora Asahi Remix as development server.

## Services

### Forgejo (Git Service)
- **Port**: 3000 (localhost only)
- **Type**: systemd user service
- **Data**: `/mnt/data/srv/forgejo`

### Vaultwarden (Password Manager)
- **Port**: 8000 (localhost only)
- **Type**: systemd user service
- **Data**: `/mnt/data/srv/vaultwarden`

### PostgreSQL (Database)
- **Port**: 5432 (localhost only)
- **Type**: system service
- **Data**: `/var/lib/pgsql`

### Ollama (LLM Inference)
- **Port**: 11434 (localhost only)
- **Type**: systemd user service
- **Data**: `/mnt/data/srv/ollama`

## Architecture

All services bind to localhost (127.0.0.1). External access via SSH tunneling:

ssh -L 3000:localhost:3000 user@server

## Installation

See individual service directories for installation scripts and configuration.

## Monitoring

systemctl --user status forgejo
systemctl --user status vaultwarden
systemctl --user status ollama
sudo systemctl status postgresql


## Backup

Automated backups via systemd timers. See `scripts/backup/`.

## License

MIT


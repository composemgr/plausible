## 👋 Welcome to plausible 🚀

Privacy-friendly Google Analytics alternative

## 📋 Description

Privacy-friendly Google Analytics alternative

## 🚀 Services

- **app**: plausible/analytics:latest

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/plausible/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/plausible" ~/.local/srv/docker/plausible
cd ~/.local/srv/docker/plausible
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install plausible
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
BASE_HOST_NAME=plausible
BASE_DOMAIN_NAME=example.com
APP_SECRET_KEY=replace-with-a-random-secret-key-min-32-chars
DB_CREATE_DATABASE_NAME=plausible
DB_USER_NAME=plausible
DB_USER_PASS=replace-with-a-random-password
EMAIL_SERVER_HOST=localhost
EMAIL_SERVER_PORT=587
EMAIL_SERVER_LOGIN_NAME=
EMAIL_SERVER_LOGIN_PASS=replace-with-a-random-password
EMAIL_SERVER_MAIL_FROM=no-reply@plausible.example.com
DISABLE_REGISTRATION=true
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64305` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64305

## 📂 Volumes

- `./volumes/data/db/postgres/plausible` - Data storage
- `./volumes/data/db/clickhouse/plausible` - Data storage
- `./volumes/config/plausible/clickhouse` - Data storage

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄

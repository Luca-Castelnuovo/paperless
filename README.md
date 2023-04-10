# paperless
Paperless-NGX for Castelnuovo

### Server installation

```bash
apt update -y && apt upgrade -y

curl -fsSL https://get.docker.com -o get-docker.sh
./get-docker.sh && rm get-docker.sh

git clone https://github.com/Luca-Castelnuovo/paperless

cd paperless && mv * .. && mv .* ..
cd .. && rmdir paperless
```

### Docker installation

```bash
docker network create traefik-proxy

# Authelia
cd authelia
cp .env.example .env && nano .env
docker compose up -d && cd ..

# Traefik
cd traefik
cp .env.example .env && nano .env
touch config/acme.json && chmod 600 config/acme.json
docker compose up -d && cd ..

# Paperless
cd paperless
cp .env.example .env && nano .env
docker compose up -d && cd ..

# Watchtower
cd watchtower
cp .env.example .env && nano .env
docker compose up -d && cd ..
```

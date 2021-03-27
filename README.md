# Traefik examples

Examples to use [Traefik reverse proxy](https://traefik.io/) with `docker-compose`.

## Examples

- `whoami`: Single service with `traefik/whoami`
- `nginx`: Multiple services with `nginx`
- `https-with-traefik-default-cert`: https (TLS) using Traefik default self-signed certificate
- `https-with-self-signed-cert`: https (TLS) using self-signed certificate
- `https-with-letsencrypt`: https (TLS) using Let's Encrypt

## Usage

### `whoami`

```bash
cd repo-root/whoami/
docker-compose up -d
```

```bash
http 127.0.0.1 Host:whoami.docker.localhost
```

### `nginx`

```bash
cd repo-root/nginx/
docker-compose up -d
```

```bash
http 127.0.0.1 Host:tako.example.com
http 127.0.0.1 Host:ika.example.com
```

### `https-with-traefik-default-cert`

```bash
cd repo-root/https-with-traefik-default-cert/
echo 'DOMAIN=localhost' > .env
docker-compose up -d
```

```bash
http --verify=no --default-scheme=https localhost
```

### `https-with-self-signed-cert`

```bash
cd repo-root/https-with-self-signed-cert/
echo 'DOMAIN=localhost' > .env
docker-compose up -d
```

```bash
http --verify=no --default-scheme=https localhost
```

The certificate is stored in a Docker volume named `certs`. Please clear the volume once you've finished.

```bash
docker volume rm https-with-self-signed-cert_certs
```

### `https-with-letsencrypt`

You need to make the server public first so that the Let's Encrypt server can access your server.

```bash
cd repo-root/https-with-letsencrypt/
echo 'DOMAIN=mydomain.com' > .env
docker-compose up -d
```

```bash
http --verify=no --default-scheme=https [IP] Host:mydomain.com
```

If you want to get a valid certificate, comment out the line for `caServer`:

`traefik.yml`:

```yaml
      # caServer: "https://acme-staging-v02.api.letsencrypt.org/directory"
```

The certificate is stored in a Docker volume named `letsencrypt`. Please clear the volume once you've finished.

```bash
docker volume rm https-with-letsencrypt_letsencrypt
```

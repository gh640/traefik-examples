# Traefik examples

Examples to use [Traefik reverse proxy](https://traefik.io/) with `docker-compose`.

## Examples

- `whoami`: Single service with `traefik/whoami`
- `nginx`: Multiple services with `nginx`

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

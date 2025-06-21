# 🐳 Docker Commands Guide

Simple reference for Docker host-container mapping.

## Volume Mounting

**Map files/folders from host to container**

```bash
docker run -v .:/var/www my-app
```

- Host: `.` (current folder)
- Container: `/var/www`

## Port Forwarding

**Access container services from host**

```bash
docker run -p 8080:80 nginx
```

- Host: `8080`
- Container: `80`
- Access via `localhost:8080`

## Configuration Files

**Mount config files**

```bash
docker run -v ./nginx.conf:/etc/nginx/nginx.conf nginx
```

- Host: `./nginx.conf`
- Container: `/etc/nginx/nginx.conf`

## Dockerfile Copy

**Copy files during build**

```dockerfile
COPY ./src /var/www
```

- Host: `./src`
- Container: `/var/www`

## Docker Compose

**YAML configuration**

```yaml
services:
  web:
    image: nginx
    volumes:
      - .:/var/www
    ports:
      - "8080:80"
```

## Environment Variables

**Load environment file**

```bash
docker run --env-file .env my-app
```

- Host: `.env` file
- Container: Available as ENV variables

## Quick Commands

```bash
# Build
docker build -t my-app .

# Run
docker run -d -p 8080:80 -v .:/app my-app

# Stop
docker stop container-name

# Remove
docker rm container-name
```

---

**Remember**: Host (outside) → Container (inside)
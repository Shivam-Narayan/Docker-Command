# 🐳 Docker CLI Reference

> A complete quick-reference for containers, images, volumes, networks, and Compose.

---

## Table of Contents

- [Container Management](#container-management)
- [Logs](#logs)
- [Inspect & Monitor](#inspect--monitor)
- [Shell Access](#shell-access)
- [Images](#images)
- [Networks](#networks)
- [Volumes](#volumes)
- [Copy Files](#copy-files)
- [Cleanup & Disk Space](#cleanup--disk-space)
- [Docker Compose](#docker-compose)
- [Quick Reference](#quick-reference)

---

## Container Management

```bash
# List containers
docker ps                        # Running only
docker ps -a                     # All (including stopped)

# Start / Stop / Restart
docker stop <container>
docker start <container>
docker restart <container>

# Remove
docker rm <container>            # Remove a stopped container
docker container prune           # Remove all stopped containers
```

---

## Logs

```bash
docker logs <container>          # View logs
docker logs -f <container>       # Follow (tail) logs in real time
```

---

## Inspect & Monitor

```bash
docker inspect <container|image> # Full JSON details
docker stats                     # Live CPU & memory usage
docker top <container>           # Running processes inside container
docker port <container>          # Mapped ports
docker events                    # Live stream of Docker daemon events
```

---

## Shell Access

```bash
docker exec -it <container> sh   # Enter container shell (sh)
docker exec -it <container> bash # Enter container shell (bash)
```

---

## Images

```bash
# List & Pull
docker images                    # List local images
docker image ls                  # Same as above
docker pull <image:tag>          # Pull image from registry
docker build -t myimg:latest .   # Build image from Dockerfile

# Remove
docker rmi <image>               # Remove a specific image
docker image prune               # Remove dangling images
docker image prune -a            # Remove all unused images
```

---

## Networks

```bash
docker network ls                # List all networks
docker network inspect <network> # Inspect a network
```

---

## Volumes

```bash
docker volume ls                 # List all volumes
docker volume inspect <volume>   # Inspect a volume
docker volume prune              # Remove unused volumes
```

---

## Copy Files

```bash
# Container → Host
docker cp <container>:/path/in/container ./localpath

# Host → Container
docker cp ./localfile <container>:/path/in/container
```

---

## Cleanup & Disk Space

```bash
docker system df                          # Show disk usage breakdown
docker system prune                       # Remove unused containers, networks, images
docker system prune -a --volumes          # Aggressive — also removes unused volumes
docker builder prune                      # Clear build cache
docker container prune                    # Remove all stopped containers
docker image prune -a                     # Remove all unused images
docker volume prune                       # Remove unused volumes
```

> ⚠️ `docker system prune -a --volumes` is destructive. Double-check before running in production.

---

## Docker Compose

```bash
# Core
docker compose up -d             # Start services in detached mode
docker compose down              # Stop and remove containers
docker compose ps                # List service containers
docker compose logs -f           # Follow logs for all services
docker compose restart           # Restart all services

# Extras
docker compose config            # Show resolved / merged config
docker compose exec <service> sh # Open shell in a running service
```

---

## Quick Reference

| Task                        | Command                                  |
|-----------------------------|------------------------------------------|
| See all containers          | `docker ps -a`                           |
| Check disk usage            | `docker system df`                       |
| Nuke all unused resources   | `docker system prune -a --volumes`       |
| Watch live resource usage   | `docker stats`                           |
| Tail container logs         | `docker logs -f <container>`             |
| Debug a running container   | `docker exec -it <container> sh`         |
| Inspect full config         | `docker inspect <container>`             |
| List images                 | `docker images`                          |
| Remove stopped containers   | `docker container prune`                 |
| Clear build cache           | `docker builder prune`                   |

---

> **Tip:** Replace `<container>` with either the container **name** or **ID**.  
> Use `docker ps -a` to find both.

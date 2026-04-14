# 🐳 Docker Commands Reference

A quick-reference guide to the most useful Docker CLI commands.

---

## 📋 Container Management

### List Containers
```bash
docker ps                  # Running containers only
docker ps -a               # All containers (including stopped)
```

### Start / Stop / Restart
```bash
docker stop <container>
docker start <container>
docker restart <container>
```

### Remove Containers
```bash
docker rm <container>      # Remove a stopped container
docker container prune     # Remove all stopped containers
```

---

## 📜 Logs

```bash
docker logs <container>           # View logs
docker logs -f <container>        # Follow (tail) logs in real time
```

---

## 🔍 Inspect & Monitor

```bash
docker inspect <container-or-image>    # Full JSON details
docker stats                           # Live CPU & memory usage
docker top <container>                 # Running processes inside container
docker port <container>                # Mapped ports
docker events                          # Live stream of Docker daemon events
```

---

## 💻 Shell Access

```bash
docker exec -it <container> sh         # Enter container (sh)
docker exec -it <container> bash       # Enter container (bash)
```

---

## 📦 Images

### List & Pull
```bash
docker images                          # List local images
docker image ls                        # Same as above
docker pull <image:tag>                # Pull image from registry
docker build -t myimg:latest .         # Build image from Dockerfile
```

### Remove Images
```bash
docker rmi <image>                     # Remove a specific image
docker image prune                     # Remove dangling (unused) images
docker image prune -a                  # Remove ALL unused images
```

---

## 🌐 Networks

```bash
docker network ls                      # List all networks
docker network inspect <network>       # Inspect a network
```

---

## 💾 Volumes

```bash
docker volume ls                       # List all volumes
docker volume inspect <volume>         # Inspect a volume
docker volume prune                    # Remove unused volumes
```

---

## 📁 Copy Files

```bash
# Container → Host
docker cp <container>:/path/in/container ./localpath

# Host → Container
docker cp ./localfile <container>:/path/in/container
```

---

## 🧹 Cleanup & Disk Space

```bash
docker system df                       # Show disk usage
docker system prune                    # Remove unused containers, networks, images
docker system prune -a --volumes       # Aggressive: also removes unused volumes
docker builder prune                   # Clear build cache
```

---

## 🐙 Docker Compose

### Core Commands
```bash
docker compose up -d                   # Start services in detached mode
docker compose down                    # Stop and remove containers
docker compose ps                      # List service containers
docker compose logs -f                 # Follow logs for all services
docker compose restart                 # Restart all services
```

### Extras
```bash
docker compose config                  # Show resolved/merged config
docker compose exec <service> sh       # Shell into a running service
```

---

## 💡 Tips

| Task | Command |
|---|---|
| Nuke everything unused | `docker system prune -a --volumes` |
| Check what's eating disk | `docker system df` |
| Watch container in real time | `docker stats` + `docker logs -f` |
| Debug a running container | `docker exec -it <container> sh` |
| See how a container is configured | `docker inspect <container>` |

---

> **Note:** Replace `<container>` with either the container name or ID. Use `docker ps -a` to find them.

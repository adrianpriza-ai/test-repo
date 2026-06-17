# Docker Cheatsheet

Panduan lengkap penggunaan **Docker** dan **Docker Compose**.

---

## 🐳 Basic Commands

```bash
docker ps                    # Lihat container yang berjalan
docker ps -a                 # Lihat semua container (termasuk yang stop)
docker images                # Lihat daftar image
docker pull <image>          # Download image
docker run <image>           # Jalankan container dari image
docker run -d <image>        # Jalankan di background
docker run -p 8080:80 <image> # Map port 8080 host ke 80 container
docker run -v /host:/container <image> # Mount volume
docker exec -it <container> bash # Masuk ke container
docker stop <container>      # Stop container
docker start <container>     # Start container
docker restart <container>   # Restart container
docker rm <container>        # Hapus container
docker rmi <image>           # Hapus image
docker system prune          # Cleanup semua yang tidak terpakai
```

---

## 🎼 Docker Compose

```bash
docker-compose up            # Start services
docker-compose up -d         # Start di background
docker-compose down          # Stop dan hapus services
docker-compose ps            # Lihat status services
docker-compose logs          # Lihat logs
docker-compose logs -f       # Follow logs
docker-compose build         # Build images
docker-compose restart       # Restart services
```

---

## 📄 Dockerfile Example

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🔧 Common Docker Operations

### Build Image from Dockerfile

```bash
docker build -t my-app .     # Build dengan tag 'my-app'
docker build -t my-app:v1.0 . # Build dengan versi spesifik
```

### Run with Environment Variables

```bash
docker run -e NODE_ENV=production -e PORT=3000 my-app
```

### View Container Logs

```bash
docker logs <container>      # Lihat logs
docker logs -f <container>   # Follow logs (live)
docker logs --tail 100 <container> # 100 baris terakhir
```

### Copy Files to/from Container

```bash
docker cp file.txt <container>:/path/    # Copy ke container
docker cp <container>:/path/file.txt .   # Copy dari container
```

### Inspect Container/Image

```bash
docker inspect <container>   # Detail container
docker inspect <image>       # Detail image
```

---

## 🧹 Cleanup Commands

```bash
docker container prune       # Hapus semua stopped containers
docker image prune           # Hapus dangling images
docker image prune -a        # Hapus semua unused images
docker volume prune          # Hapus unused volumes
docker system prune -a       # Hapus semua yang tidak terpakai
```

---

## 🌐 Network

```bash
docker network ls            # List networks
docker network create mynet  # Buat network baru
docker network inspect mynet # Detail network
docker network connect mynet <container> # Connect container ke network
docker network disconnect mynet <container> # Disconnect container
```

---

## 💾 Volume

```bash
docker volume ls             # List volumes
docker volume create myvol   # Buat volume baru
docker volume inspect myvol  # Detail volume
docker volume rm myvol       # Hapus volume
```

---

> Last Updated: $(date +%Y-%m-%d)

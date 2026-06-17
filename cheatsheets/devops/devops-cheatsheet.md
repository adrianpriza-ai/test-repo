# DevOps & CI/CD Cheatsheet

Panduan lengkap untuk **DevOps tools**, **CI/CD**, dan **monitoring**.

---

## 🔄 GitHub Actions

### Debugging

```bash
# Enable debug logging
gh run view <id> --log       # View workflow logs
gh workflow run <name>       # Trigger workflow manually
```

### Common Environment Variables

```
CI=true                      # Continuous Integration flag
NODE_ENV=production          # Node environment
PYTHONPATH=/path/to/module   # Python module path
PATH=/usr/local/bin:$PATH    # Executable search path
HOME=/home/user              # Home directory
PWD=/current/working/dir     # Current directory
GITHUB_WORKSPACE             # Workspace directory
GITHUB_SHA                   # Commit SHA
GITHUB_REF                   # Branch/Tag ref
GITHUB_ACTOR                 # Username triggering workflow
```

### Workflow Commands

```yaml
# In workflow file
run: |
  echo "Hello from GitHub Actions"
  npm install
  npm test
  
# With working directory
- name: Build
  working-directory: ./subdir
  run: npm run build

# With environment variables
- name: Deploy
  env:
    API_KEY: ${{ secrets.API_KEY }}
  run: ./deploy.sh
```

---

## 🐳 Docker in CI/CD

### Common Docker Commands in CI

```bash
# Build image
docker build -t my-app:${{ github.sha }} .

# Run tests in container
docker run --rm my-app:${{ github.sha }} npm test

# Push to registry
docker push my-app:${{ github.sha }}

# Cleanup
docker system prune -f
```

### Docker Compose in CI

```bash
# Start services
docker-compose up -d

# Run tests against services
docker-compose run --rm app npm test

# Stop and cleanup
docker-compose down -v
```

---

## ☸️ Kubernetes Basics

### kubectl Commands

```bash
kubectl get pods             # List pods
kubectl get deployments      # List deployments
kubectl get services         # List services
kubectl get namespaces       # List namespaces
kubectl describe pod <name>  # Pod details
kubectl logs <pod>           # View logs
kubectl exec -it <pod> bash  # Enter pod
kubectl apply -f file.yaml   # Apply configuration
kubectl delete -f file.yaml  # Delete resources
kubectl rollout restart deployment/<name>  # Restart deployment
```

### Common Operations

```bash
# Scale deployment
kubectl scale deployment/my-app --replicas=3

# Port forward
kubectl port-forward pod/my-pod 8080:80

# Copy files
kubectl cp file.txt pod:/path/
kubectl cp pod:/path/file.txt .

# View events
kubectl get events --sort-by='.lastTimestamp'
```

---

## 🔍 Monitoring & Logging

### htop (Process Monitor)

```bash
htop                         # Launch htop
F6                           # Sort by column
F3                           # Search process
F9                           # Kill process
q                            # Quit
```

### iostat (I/O Statistics)

```bash
iostat                       # CPU dan I/O stats
iostat -x 2                  # Extended stats setiap 2 detik
iostat -d                    # Device utilization
```

### vmstat (Virtual Memory Stats)

```bash
vmstat                       # Memory, swap, I/O stats
vmstat 2                     # Update setiap 2 detik
vmstat -s                    # Summary statistics
```

### ncdu (Disk Usage Analyzer)

```bash
ncdu                         # Analyze disk usage
ncdu /path                   # Analyze specific directory
```

### journalctl (Systemd Logs)

```bash
journalctl                   # View all logs
journalctl -f                # Follow logs
journalctl -u service        # Service logs
journalctl --since "1 hour ago"  # Last hour
journalctl -p err            # Error level only
```

### Prometheus/Grafana Queries

```promql
# CPU usage
rate(node_cpu_seconds_total{mode="user"}[5m])

# Memory usage
node_memory_MemUsed_bytes / node_memory_MemTotal_bytes

# Disk I/O
rate(node_disk_read_bytes_total[5m])

# Network traffic
rate(node_network_receive_bytes_total[5m])
```

---

## 🔐 SSH & Security

### SSH Commands

```bash
ssh user@host                # Connect ke remote
ssh -p 2222 user@host        # Connect dengan port custom
ssh-keygen -t ed25519        # Generate SSH key
ssh-copy-id user@host        # Copy public key ke remote
scp file user@host:/path     # Copy file ke remote
scp user@host:/path file     # Copy file dari remote
rsync -avz src/ dst/         # Sync files (lebih efisien)
ssh -L 8080:localhost:80 user@host  # Port forwarding
```

### SSH Config (~/.ssh/config)

```
Host myserver
    HostName server.example.com
    User myuser
    Port 2222
    IdentityFile ~/.ssh/id_ed25519
```

### GPG Encryption

```bash
gpg --generate-key           # Generate GPG key
gpg --list-keys              # List keys
gpg --encrypt --recipient <email> file # Encrypt file
gpg --decrypt file.gpg       # Decrypt file
gpg --export <email>         # Export public key
gpg --import key.asc         # Import key
```

---

## 📊 Performance Tuning

### Quick Diagnostics

```bash
# Check load average
uptime

# Check memory
free -h

# Check disk space
df -h

# Check I/O wait
iostat -x 2

# Check network connections
ss -s

# Find slow processes
ps aux --sort=-%cpu | head
```

### ulimit (Resource Limits)

```bash
ulimit -a                    # Show all limits
ulimit -n                    # Max open files
ulimit -u                    # Max user processes
ulimit -n 65536              # Set max open files
```

### sysctl (Kernel Parameters)

```bash
sysctl -a                    # Show all parameters
sysctl net.ipv4.ip_forward   # Check IP forwarding
sysctl -w net.ipv4.ip_forward=1  # Enable IP forwarding
```

---

## 🎯 Quick Reference

| Tool | Command | Description |
|------|---------|-------------|
| kubectl | `kubectl get pods` | List Kubernetes pods |
| docker | `docker ps` | Running containers |
| systemctl | `systemctl status svc` | Service status |
| journalctl | `journalctl -f` | Follow logs |
| ssh | `ssh user@host` | Remote connection |
| rsync | `rsync -av src/ dst/` | Sync files |
| htop | `htop` | Process monitor |
| ncdu | `ncdu` | Disk usage analyzer |

---

## 🔧 Useful Scripts

### Health Check Script

```bash
#!/bin/bash
echo "=== System Health Check ==="
echo "Uptime: $(uptime)"
echo "Memory: $(free -h | grep Mem)"
echo "Disk: $(df -h / | tail -1)"
echo "Load: $(cat /proc/loadavg)"
```

### Log Rotation

```bash
# Manual log rotation
logrotate -f /etc/logrotate.conf

# Check logrotate status
logrotate -d /etc/logrotate.conf
```

---

> Last Updated: 17-Juni-2026

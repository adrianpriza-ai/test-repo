# Linux Commands Cheatsheet

Panduan lengkap **Linux commands** untuk daily use.

---

## 📁 File & Directory

```bash
ls -la                       # List semua file (termasuk hidden)
cd <dir>                     # Pindah directory
pwd                          # Tampilkan directory saat ini
mkdir <nama>                 # Buat directory baru
rm <file>                    # Hapus file
rm -rf <dir>                 # Hapus directory dan isinya
cp <src> <dst>               # Copy file
cp -r <src> <dst>            # Copy directory
mv <src> <dst>               # Pindah/rename file
touch <file>                 # Buat file kosong
cat <file>                   # Lihat isi file
less <file>                  # Baca file halaman per halaman
head -n 10 <file>            # 10 baris pertama
tail -n 10 <file>            # 10 baris terakhir
tail -f <file>               # Follow file (live)
ln -s <target> <link>        # Buat symbolic link
chmod 755 <file>             # Ubah permission (rwxr-xr-x)
chmod +x <file>              # Tambah execute permission
chown user:group <file>      # Ubah owner dan group
chown -R user:group <dir>    # Recursive change ownership
```

---

## 🔍 Search & Find

```bash
find . -name "*.txt"         # Cari file berdasarkan nama
grep "pattern" <file>        # Cari text dalam file
grep -r "pattern" .          # Cari recursive
grep -i "pattern"            # Case insensitive
grep -v "pattern"            # Exclude pattern
grep -n "pattern"            # Show line numbers
locate <file>                # Cari file (lebih cepat)
which <command>              # Lokasi executable
whereis <command>            # Lokasi binary, source, man
type <command>               # Tipe command (alias, function, binary)
```

---

## ⚙️ Process & System

```bash
ps aux                       # Lihat semua process
top                          # Monitor process real-time
htop                         # Top dengan UI lebih baik
kill <pid>                   # Kill process
kill -9 <pid>                # Force kill
pkill <name>                 # Kill by name
pgrep <name>                 # Find PID by name
df -h                        # Disk usage
du -sh <dir>                 # Ukuran directory
free -h                      # Memory usage
uname -a                     # Info sistem
uptime                       # Lama sistem berjalan
whoami                       # User saat ini
hostname                     # Nama host
date                         # Tanggal dan waktu
cal                          # Kalender
history                      # Riwayat command
```

---

## 🌐 Network

```bash
ping <host>                  # Test koneksi
curl <url>                   # HTTP request
wget <url>                   # Download file
netstat -tulpn               # Lihat port yang terbuka
ss -tulpn                    # Alternatif netstat (lebih cepat)
ip addr                      # Lihat IP address
ip route                     # Lihat routing table
traceroute <host>            # Trace route ke host
nslookup <domain>            # DNS lookup
dig <domain>                 # DNS lookup (detail)
hostname -I                  # Show all IP addresses
arp -a                       # Show ARP table
```

---

## 🗜️ Compression

```bash
tar -czvf archive.tar.gz <dir>  # Compress ke tar.gz
tar -xzvf archive.tar.gz        # Extract tar.gz
tar -cjvf archive.tar.bz2 <dir> # Compress ke tar.bz2
tar -xjvf archive.tar.bz2       # Extract tar.bz2
zip -r archive.zip <dir>        # Compress ke zip
unzip archive.zip               # Extract zip
gzip <file>                     # Compress file
gunzip <file.gz>                # Decompress file
```

---

## 👥 User Management

```bash
adduser <username>           # Buat user baru
deluser <username>           # Hapus user
passwd <username>            # Ganti password user
usermod -aG sudo <username>  # Tambah ke sudo group
su - <username>              # Switch user
sudo <command>               # Run command sebagai root
groups                       # Lihat group user
id                           # User dan group ID
```

---

## 📊 System Monitoring

```bash
top                          # Process monitor
htop                         # Enhanced top
vmstat                       # Virtual memory stats
iostat                       # I/O statistics
mpstat                       # CPU statistics
sar                          # System activity reporter
dmesg                        # Kernel messages
journalctl                   # Systemd logs
journalctl -f                # Follow logs
```

---

## 🔧 Useful One-Liners

```bash
# Count lines in all files
find . -type f | xargs wc -l

# Find and delete all .tmp files
find . -name "*.tmp" -delete

# Backup file with timestamp
cp file.txt file.txt.$(date +%Y%m%d_%H%M%S)

# Check if port is in use
lsof -i :8080

# Get public IP
curl ifconfig.me

# Show disk usage by directory
du -h --max-depth=1 | sort -hr

# Find large files (>100MB)
find . -type f -size +100M

# Monitor file changes
watch -n 2 'ls -la'
```

---

## 🎯 Quick Reference

| Command | Description |
|---------|-------------|
| `ls -la` | List all files including hidden |
| `cd ..` | Go up one directory |
| `pwd` | Print working directory |
| `cp -r src dst` | Copy directory recursively |
| `rm -rf dir` | Remove directory and contents |
| `chmod +x file` | Make file executable |
| `grep -r "text" .` | Search text recursively |
| `ps aux | grep <name>` | Find process by name |
| `kill -9 <pid>` | Force kill process |
| `df -h` | Show disk space |
| `free -h` | Show memory usage |
| `curl -I <url>` | GET request headers only |

---

> Last Updated: $(date +%Y-%m-%d)

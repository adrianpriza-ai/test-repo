# Git & GitHub CLI (gh) Cheatsheet

Panduan lengkap penggunaan **Git** dan **GitHub CLI (gh)** dari terminal.

---

## 📦 Git

### Setup Awal
```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@kamu.com"
```

### Membuat & Clone Repo
```bash
git init                      # Buat repo baru di folder saat ini
git clone <url>               # Clone repo dari remote
```

### Staging & Commit
```bash
git status                    # Cek status file
git add .                     # Staging semua perubahan
git add <file>                # Staging file tertentu
git commit -m "pesan"         # Simpan commit
```

### Remote
```bash
git remote add origin <url>   # Hubungkan ke remote
git remote -v                 # Lihat daftar remote
git remote set-url origin <url> # Ganti URL remote
```

### Push & Pull
```bash
git push origin master        # Upload ke remote
git pull origin master        # Download + merge dari remote
git fetch origin              # Download tanpa merge
git merge origin/master       # Merge secara manual
```

### Branch
```bash
git branch                    # Lihat daftar branch
git branch -a                 # Termasuk branch remote
git branch <nama>             # Buat branch baru
git checkout <nama>           # Pindah ke branch
git checkout -b <nama>        # Buat + langsung pindah
git merge <nama>              # Gabung branch ke branch aktif
git branch -d <nama>          # Hapus branch
```

### Riwayat & Perubahan
```bash
git log                       # Lihat riwayat commit
git log --oneline             # Ringkas satu baris
git diff                      # Lihat perubahan belum di-stage
git diff --staged             # Lihat perubahan sudah di-stage
```

### Undo
```bash
git restore <file>            # Batalkan perubahan file
git restore --staged <file>   # Unstage file yang sudah di-stage
git reset HEAD~1              # Batalkan commit terakhir (keep changes)
git reset --hard HEAD~1       # Batalkan commit terakhir (discard changes)
git revert <commit-hash>      # Buat commit baru yang membalik commit tertentu
git stash                     # Simpan perubahan sementara
git stash list                # Lihat daftar stash
git stash pop                 # Ambil kembali stash terakhir
git stash drop                # Hapus stash terakhir
git stash apply               # Terapkan stash tanpa menghapusnya
git stash branch <nama>       # Buat branch dari stash
```

### Cherry-Pick & Rebase
```bash
git cherry-pick <commit-hash> # Terapkan commit dari branch lain
git rebase <branch>           # Rebase branch aktif ke branch lain
git rebase -i HEAD~3          # Interactive rebase 3 commit terakhir
git rebase --abort            # Batalkan rebase yang sedang berjalan
git rebase --continue         # Lanjutkan rebase setelah resolve conflict
```

### Tagging
```bash
git tag                       # Lihat daftar tag
git tag -a v1.0 -m "versi 1.0" # Buat annotated tag
git tag v1.0                  # Buat lightweight tag
git push origin v1.0          # Push tag ke remote
git push --tags               # Push semua tag
git tag -d v1.0               # Hapus tag lokal
git push origin --delete v1.0 # Hapus tag remote
```

### Cleanup & Maintenance
```bash
git gc                        # Garbage collection, optimasi repo
git fsck                      # Cek integritas repo
git prune                     # Hapus object yang tidak terhubung
git reflog                    # Lihat riwayat semua referensi
git clean -n                  # Preview file yang akan dihapus (dry run)
git clean -f                  # Hapus untracked files
git clean -fd                 # Hapus untracked files dan folder
```

### Shortcut (Alias)
```bash
# Tambah alias push-all
git config --global alias.sync '!git add . && git commit -m "update" && git push origin master'

# Pakai
git sync
```

---

## ⚡ GitHub CLI (gh)

### Install & Login
```bash
sudo pacman -S github-cli     # Install (Arch/EndeavourOS)
gh auth login                 # Login ke GitHub
```

### Repo
```bash
gh repo create <nama>         # Buat repo baru
gh repo create <nama> --public   # Buat repo publik
gh repo clone <nama>          # Clone repo
gh repo view                  # Lihat info repo
gh repo delete <nama>         # Hapus repo
```

### Pull Request
```bash
gh pr create                  # Buat pull request
gh pr list                    # Lihat daftar PR
gh pr view <nomor>            # Detail PR
gh pr merge <nomor>           # Merge PR
gh pr review <nomor>          # Review PR
gh pr close <nomor>           # Tutup PR
```

### Issues
```bash
gh issue create               # Buat issue baru
gh issue list                 # Lihat daftar issue
gh issue view <nomor>         # Detail issue
gh issue close <nomor>        # Tutup issue
gh issue reopen <nomor>       # Buka kembali issue
```

### GitHub Actions / Workflow
```bash
gh run list                   # Lihat daftar workflow run
gh run view <id>              # Detail run
gh run watch <id>             # Pantau run secara live
gh workflow list              # Lihat daftar workflow
gh workflow run <nama>        # Trigger workflow manual
```

### Release
```bash
gh release create <tag>       # Buat release baru
gh release list               # Lihat daftar release
gh release view <tag>         # Detail release
gh release delete <tag>       # Hapus release
```

### Gist
```bash
gh gist create <file>         # Buat gist dari file
gh gist list                  # Lihat daftar gist
gh gist view <id>             # Lihat isi gist
gh gist delete <id>           # Hapus gist
```

### SSH Key
```bash
gh ssh-key add ~/.ssh/id_ed25519.pub   # Tambah SSH key ke GitHub
gh ssh-key list                        # Lihat daftar SSH key
gh ssh-key delete <id>                 # Hapus SSH key
```

### Codespaces
```bash
gh codespace create                    # Buat codespace baru
gh codespace list                      # Lihat daftar codespace
gh codespace delete <nama>             # Hapus codespace
gh codespace ssh <nama>                # SSH ke codespace
gh codespace cp <file> <nama>:<path>   # Copy file ke codespace
gh codespace cp <nama>:<path> <file>   # Copy file dari codespace
```

### Project (GitHub Projects)
```bash
gh project list                        # Lihat daftar project
gh project view <number>               # Detail project
gh project item-list <number>          # Lihat item dalam project
gh project item-create <number>        # Tambah item ke project
gh project item-edit --field <name>    # Edit field item
```

### Variable & Secret (untuk Actions)
```bash
gh variable set <name>                 # Set variable untuk Actions
gh variable list                       # Lihat daftar variable
gh variable delete <name>              # Hapus variable
gh secret set <name>                   # Set secret untuk Actions
gh secret list                         # Lihat daftar secret
gh secret delete <name>                # Hapus secret
```

### Label
```bash
gh label list                          # Lihat daftar label
gh label create <nama>                 # Buat label baru
gh label edit <nama>                   # Edit label
gh label delete <nama>                 # Hapus label
```

### Cache (Actions Cache)
```bash
gh cache list                          # Lihat daftar cache Actions
gh cache delete <id>                   # Hapus cache
gh cache delete --all                  # Hapus semua cache
```

---

## 🔄 Alur Kerja Umum

### Update & Upload Perubahan
```bash
git pull origin master        # Ambil perubahan terbaru
# ... edit file ...
git add .
git commit -m "pesan"
git push origin master
```

### Buat Repo Baru Langsung dari Terminal
```bash
mkdir nama-project && cd nama-project
git init
gh repo create nama-project --public
git add .
git commit -m "first commit"
git push -u origin master
```

### Fork & Contribute ke Repo Orang
```bash
gh repo fork <repo>                   # Fork repo orang lain
gh repo sync                          # Sync fork dengan upstream
gh pr create --base <branch>          # Buat PR ke branch tertentu
```

### Compare Branch / Commit
```bash
git diff <branch1>..<branch2>         # Bandingkan dua branch
git diff <commit1>..<commit2>         # Bandingkan dua commit
git log <branch1>.. <branch2>         # Lihat commit yang berbeda
```

### Blame & Search
```bash
git blame <file>                      # Lihat siapa yang mengubah tiap baris
git log -S"<keyword>"                 # Cari commit yang mengubah keyword
git log --grep="<pesan>"              # Cari commit berdasarkan pesan
```

### Submodule
```bash
git submodule add <url>               # Tambah submodule
git submodule update --init           # Init dan update submodule
git submodule update --remote         # Update submodule ke versi terbaru
```

---

## 💡 Tips & Tricks

### Git Config per Project
```bash
# Override config global untuk project tertentu
git config user.email "project@specific.com"
git config user.name "Project User"
```

### Melihat Statistik
```bash
git shortlog -sn                      # Jumlah commit per author
git count-objects -v                  # Statistik object git
git ls-files | xargs wc -l            # Hitung total baris kode
```

### Quick Fixes
```bash
# Amend commit terakhir (ganti pesan atau tambah file)
git commit --amend -m "pesan baru"

# Fix typo di commit terakhir tanpa mengubah timestamp
git commit --amend --no-edit
```

### Hook Scripts
```bash
# Contoh: pre-commit hook untuk run test
# Edit file: .git/hooks/pre-commit
#!/bin/bash
npm test
```

---

> Dibuat dengan ❤️ menggunakan Git & GitHub CLI

---

## 🐳 Docker

### Basic Commands
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

### Docker Compose
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

### Dockerfile Example
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

## 🐧 Linux Commands

### File & Directory
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
```

### Search & Find
```bash
find . -name "*.txt"         # Cari file berdasarkan nama
grep "pattern" <file>        # Cari text dalam file
grep -r "pattern" .          # Cari recursive
grep -i "pattern"            # Case insensitive
grep -v "pattern"            # Exclude pattern
locate <file>                # Cari file (lebih cepat)
which <command>              # Lokasi executable
whereis <command>            # Lokasi binary, source, man
```

### Permissions & Ownership
```bash
chmod 755 <file>             # Ubah permission (rwxr-xr-x)
chmod +x <file>              # Tambah execute permission
chown user:group <file>      # Ubah owner dan group
chown -R user:group <dir>    # Recursive change ownership
```

### Process & System
```bash
ps aux                       # Lihat semua process
top                          # Monitor process real-time
htop                         # Top dengan UI lebih baik
kill <pid>                   # Kill process
kill -9 <pid>                # Force kill
df -h                        # Disk usage
du -sh <dir>                 # Ukuran directory
free -h                      # Memory usage
uname -a                     # Info sistem
uptime                       # Lama sistem berjalan
whoami                       # User saat ini
```

### Network
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
```

### Compression
```bash
tar -czvf archive.tar.gz <dir>  # Compress ke tar.gz
tar -xzvf archive.tar.gz        # Extract tar.gz
zip -r archive.zip <dir>        # Compress ke zip
unzip archive.zip               # Extract zip
gzip <file>                     # Compress file
gunzip <file.gz>                # Decompress file
```

---

## 📦 Package Managers

### apt (Debian/Ubuntu)
```bash
sudo apt update              # Update package list
sudo apt upgrade             # Upgrade packages
sudo apt install <pkg>       # Install package
sudo apt remove <pkg>        # Uninstall package
sudo apt search <keyword>    # Cari package
sudo apt show <pkg>          # Info package
```

### pacman (Arch/EndeavourOS)
```bash
sudo pacman -Syu             # Update & upgrade semua
sudo pacman -S <pkg>         # Install package
sudo pacman -R <pkg>         # Uninstall package
sudo pacman -Rs <pkg>        # Uninstall + dependencies
sudo pacman -Ss <keyword>    # Cari package
pacman -Qi <pkg>             # Info package
```

### brew (macOS/Linux)
```bash
brew install <pkg>           # Install package
brew uninstall <pkg>         # Uninstall package
brew update                  # Update brew
brew upgrade                 # Upgrade packages
brew search <keyword>        # Cari package
brew info <pkg>              # Info package
brew list                    # List installed packages
```

---

## 🟢 Node.js & npm

### Basic npm
```bash
npm init -y                  # Init project baru
npm install <pkg>            # Install package
npm install -g <pkg>         # Install global
npm uninstall <pkg>          # Uninstall package
npm update <pkg>             # Update package
npm list                     # List installed packages
npm outdated                 # Cek package yang outdated
npm audit                    # Cek security vulnerabilities
npm audit fix                # Fix vulnerabilities otomatis
```

### npm Scripts
```bash
npm start                    # Run script 'start'
npm test                     # Run script 'test'
npm run <script>             # Run custom script
npm run build                # Run script 'build'
```

### nvm (Node Version Manager)
```bash
nvm install <version>        # Install Node.js version
nvm use <version>            # Gunakan version tertentu
nvm ls                       # List installed versions
nvm current                  # Version yang aktif
nvm alias default <version>  # Set default version
```

### yarn (Alternative to npm)
```bash
yarn init                    # Init project
yarn add <pkg>               # Install package
yarn add -g <pkg>            # Install global
yarn remove <pkg>            # Uninstall package
yarn upgrade                 # Update packages
yarn list                    # List packages
```

---

## 🐍 Python

### pip (Python Package Manager)
```bash
pip install <pkg>            # Install package
pip install -r requirements.txt # Install dari file
pip uninstall <pkg>          # Uninstall package
pip list                     # List installed packages
pip freeze > requirements.txt # Export dependencies
pip show <pkg>               # Info package
pip search <keyword>         # Cari package (deprecated)
pip install --upgrade <pkg>  # Upgrade package
```

### Virtual Environment
```bash
python -m venv venv          # Buat virtual environment
source venv/bin/activate     # Activate (Linux/Mac)
venv\Scripts\activate        # Activate (Windows)
deactivate                   # Deactivate venv
```

### Python Commands
```bash
python --version             # Cek versi Python
python file.py               # Run script
python -m http.server 8000   # Simple HTTP server
python -c "print('hello')"   # Run inline command
```

---

## ☕ Java & Maven/Gradle

### Maven
```bash
mvn clean                    # Clean project
mvn compile                  # Compile project
mvn test                     # Run tests
mvn package                  # Build JAR/WAR
mvn install                  # Install ke local repo
mvn dependency:tree          # Lihat dependency tree
```

### Gradle
```bash
./gradlew clean              # Clean project
./gradlew build              # Build project
./gradlew test               # Run tests
./gradlew dependencies       # Lihat dependencies
```

---

## 🌐 Web Development

### cURL Examples
```bash
curl -X GET <url>            # GET request
curl -X POST -d "key=value" <url> # POST request
curl -H "Authorization: Bearer token" <url> # With header
curl -o file.zip <url>       # Download file
curl -I <url>                # HEAD request (headers only)
```

### HTTP Status Codes
```
200 OK                       # Success
201 Created                  # Resource created
301 Moved Permanently        # Redirect
304 Not Modified             # Cached
400 Bad Request              # Client error
401 Unauthorized             # Need authentication
403 Forbidden                # Access denied
404 Not Found                # Resource not found
500 Internal Server Error    # Server error
502 Bad Gateway              # Invalid response
503 Service Unavailable      # Server overloaded
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
```

### GPG Encryption
```bash
gpg --generate-key           # Generate GPG key
gpg --list-keys              # List keys
gpg --encrypt --recipient <email> file # Encrypt file
gpg --decrypt file.gpg       # Decrypt file
gpg --export <email>         # Export public key
```

---

## 📊 Database CLI

### PostgreSQL
```bash
psql -U username -d dbname   # Connect ke database
\l                           # List databases
\c dbname                    # Connect ke database
\dt                          # List tables
\d tablename                 # Describe table
\q                           # Quit psql
```

### MySQL/MariaDB
```bash
mysql -u username -p         # Connect ke database
SHOW DATABASES;              # List databases
USE dbname;                  # Select database
SHOW TABLES;                 # List tables
DESCRIBE tablename;          # Describe table
EXIT;                        # Quit mysql
```

### Redis
```bash
redis-cli                    # Connect ke Redis
KEYS *                       # List semua keys
GET key                      # Get value
SET key value                # Set value
DEL key                      # Delete key
FLUSHALL                     # Hapus semua data
```

### MongoDB
```bash
mongosh                      # Connect ke MongoDB
show dbs                     # List databases
use dbname                   # Select database
show collections             # List collections
db.collection.find()         # Query documents
exit                         # Quit mongosh
```

---

## 🛠️ DevTools & Utilities

### jq (JSON Processor)
```bash
cat file.json | jq '.'       # Format JSON
cat file.json | jq '.key'    # Extract field
cat file.json | jq '.[]'     # Iterate array
cat file.json | jq 'keys'    # List all keys
```

### sed (Stream Editor)
```bash
sed 's/old/new/g' file       # Replace text
sed -i 's/old/new/g' file    # Replace in-place
sed -n '5,10p' file          # Print lines 5-10
sed '/pattern/d' file        # Delete matching lines
```

### awk (Pattern Scanning)
```bash
awk '{print $1}' file        # Print first column
awk -F: '{print $1}' /etc/passwd # Custom delimiter
awk '/pattern/ {print}' file # Print matching lines
awk '{sum+=$1} END {print sum}' file # Sum column
```

### watch (Run Command Repeatedly)
```bash
watch -n 2 'command'         # Run command setiap 2 detik
watch df -h                  # Monitor disk usage
watch free -h                # Monitor memory
```

---

## 📝 Text Editors (CLI)

### Vim Basics
```
vim file                     # Buka file
i                            # Insert mode
ESC                          # Exit insert mode
:w                           # Save
:q                           # Quit
:q!                          # Quit tanpa save
:wq                          # Save & quit
dd                           # Delete line
yy                           # Copy line
p                            # Paste
/search                      # Search text
:n                           # Go to line n
:set nu                      # Show line numbers
```

### Nano Basics
```
nano file                    # Buka file
Ctrl+O                       # Save
Ctrl+X                       # Exit
Ctrl+K                       # Cut line
Ctrl+U                       # Paste
Ctrl+W                       # Search
Ctrl+\                       # Replace
```

---

## 🚀 Performance & Monitoring

### htop (Interactive Process Viewer)
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

---

## 🔄 CI/CD Tools

### GitHub Actions Debugging
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
```

---

## 💻 Shell Scripting Basics

### Variables & Conditionals
```bash
#!/bin/bash
NAME="World"
echo "Hello $NAME"

if [ $AGE -gt 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi
```

### Loops
```bash
# For loop
for i in {1..5}; do
    echo "Number $i"
done

# While loop
while [ $counter -lt 10 ]; do
    echo $counter
    ((counter++))
done
```

### Functions
```bash
greet() {
    echo "Hello $1"
}
greet "User"
```

### Useful One-Liners
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
```

---

## 🎯 Quick Reference Card

| Category | Command | Description |
|----------|---------|-------------|
| **Git** | `git status` | Cek status repository |
| **Git** | `git log --oneline` | Riwayat commit ringkas |
| **Docker** | `docker ps` | Container yang berjalan |
| **Docker** | `docker-compose up -d` | Start services |
| **Linux** | `chmod +x file` | Make executable |
| **Linux** | `grep -r "text" .` | Search text recursively |
| **npm** | `npm install -D pkg` | Install dev dependency |
| **Python** | `python -m venv venv` | Create virtual env |
| **SSH** | `ssh-keygen -t ed25519` | Generate SSH key |
| **cURL** | `curl -X POST -d data url` | POST request |
| **jq** | `jq '.key' file.json` | Extract JSON field |
| **Vim** | `:wq` | Save and quit |

---

> **Pro Tip:** Bookmark this cheatsheet or print it for quick reference! 📌
> 
> Last Updated: $(date +%Y-%m-%d)

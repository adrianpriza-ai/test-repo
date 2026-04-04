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
git reset HEAD~1              # Batalkan commit terakhir (keep changes)
git stash                     # Simpan perubahan sementara
git stash pop                 # Ambil kembali stash
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

---

> Dibuat dengan ❤️ menggunakan Git & GitHub CLI

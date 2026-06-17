# Git Cheatsheet

Panduan lengkap penggunaan **Git** dari terminal.

---

## 📦 Setup Awal

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@kamu.com"
```

---

## 📁 Membuat & Clone Repo

```bash
git init                      # Buat repo baru di folder saat ini
git clone <url>               # Clone repo dari remote
```

---

## 📝 Staging & Commit

```bash
git status                    # Cek status file
git add .                     # Staging semua perubahan
git add <file>                # Staging file tertentu
git commit -m "pesan"         # Simpan commit
```

---

## 🌐 Remote

```bash
git remote add origin <url>   # Hubungkan ke remote
git remote -v                 # Lihat daftar remote
git remote set-url origin <url> # Ganti URL remote
```

---

## ⬆️ Push & Pull

```bash
git push origin master        # Upload ke remote
git pull origin master        # Download + merge dari remote
git fetch origin              # Download tanpa merge
git merge origin/master       # Merge secara manual
```

---

## 🌿 Branch

```bash
git branch                    # Lihat daftar branch
git branch -a                 # Termasuk branch remote
git branch <nama>             # Buat branch baru
git checkout <nama>           # Pindah ke branch
git checkout -b <nama>        # Buat + langsung pindah
git merge <nama>              # Gabung branch ke branch aktif
git branch -d <nama>          # Hapus branch
```

---

## 📜 Riwayat & Perubahan

```bash
git log                       # Lihat riwayat commit
git log --oneline             # Ringkas satu baris
git diff                      # Lihat perubahan belum di-stage
git diff --staged             # Lihat perubahan sudah di-stage
```

---

## ↩️ Undo

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

---

## 🍒 Cherry-Pick & Rebase

```bash
git cherry-pick <commit-hash> # Terapkan commit dari branch lain
git rebase <branch>           # Rebase branch aktif ke branch lain
git rebase -i HEAD~3          # Interactive rebase 3 commit terakhir
git rebase --abort            # Batalkan rebase yang sedang berjalan
git rebase --continue         # Lanjutkan rebase setelah resolve conflict
```

---

## 🏷️ Tagging

```bash
git tag                       # Lihat daftar tag
git tag -a v1.0 -m "versi 1.0" # Buat annotated tag
git tag v1.0                  # Buat lightweight tag
git push origin v1.0          # Push tag ke remote
git push --tags               # Push semua tag
git tag -d v1.0               # Hapus tag lokal
git push origin --delete v1.0 # Hapus tag remote
```

---

## 🧹 Cleanup & Maintenance

```bash
git gc                        # Garbage collection, optimasi repo
git fsck                      # Cek integritas repo
git prune                     # Hapus object yang tidak terhubung
git reflog                    # Lihat riwayat semua referensi
git clean -n                  # Preview file yang akan dihapus (dry run)
git clean -f                  # Hapus untracked files
git clean -fd                 # Hapus untracked files dan folder
```

---

## ⚡ Shortcut (Alias)

```bash
# Tambah alias push-all
git config --global alias.sync '!git add . && git commit -m "update" && git push origin master'

# Pakai
git sync
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

---

> Last Updated: 17-Juni-2026

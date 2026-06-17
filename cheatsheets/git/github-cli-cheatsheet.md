# GitHub CLI (gh) Cheatsheet

Panduan lengkap penggunaan **GitHub CLI (gh)** dari terminal.

---

## 🚀 Install & Login

```bash
sudo pacman -S github-cli     # Install (Arch/EndeavourOS)
gh auth login                 # Login ke GitHub
```

---

## 📁 Repo

```bash
gh repo create <nama>         # Buat repo baru
gh repo create <nama> --public   # Buat repo publik
gh repo clone <nama>          # Clone repo
gh repo view                  # Lihat info repo
gh repo delete <nama>         # Hapus repo
```

---

## 🔀 Pull Request

```bash
gh pr create                  # Buat pull request
gh pr list                    # Lihat daftar PR
gh pr view <nomor>            # Detail PR
gh pr merge <nomor>           # Merge PR
gh pr review <nomor>          # Review PR
gh pr close <nomor>           # Tutup PR
```

---

## 🐛 Issues

```bash
gh issue create               # Buat issue baru
gh issue list                 # Lihat daftar issue
gh issue view <nomor>         # Detail issue
gh issue close <nomor>        # Tutup issue
gh issue reopen <nomor>       # Buka kembali issue
```

---

## ⚙️ GitHub Actions / Workflow

```bash
gh run list                   # Lihat daftar workflow run
gh run view <id>              # Detail run
gh run watch <id>             # Pantau run secara live
gh workflow list              # Lihat daftar workflow
gh workflow run <nama>        # Trigger workflow manual
```

---

## 📦 Release

```bash
gh release create <tag>       # Buat release baru
gh release list               # Lihat daftar release
gh release view <tag>         # Detail release
gh release delete <tag>       # Hapus release
```

---

## 📄 Gist

```bash
gh gist create <file>         # Buat gist dari file
gh gist list                  # Lihat daftar gist
gh gist view <id>             # Lihat isi gist
gh gist delete <id>           # Hapus gist
```

---

## 🔑 SSH Key

```bash
gh ssh-key add ~/.ssh/id_ed25519.pub   # Tambah SSH key ke GitHub
gh ssh-key list                        # Lihat daftar SSH key
gh ssh-key delete <id>                 # Hapus SSH key
```

---

## 💻 Codespaces

```bash
gh codespace create                    # Buat codespace baru
gh codespace list                      # Lihat daftar codespace
gh codespace delete <nama>             # Hapus codespace
gh codespace ssh <nama>                # SSH ke codespace
gh codespace cp <file> <nama>:<path>   # Copy file ke codespace
gh codespace cp <nama>:<path> <file>   # Copy file dari codespace
```

---

## 📋 Project (GitHub Projects)

```bash
gh project list                        # Lihat daftar project
gh project view <number>               # Detail project
gh project item-list <number>          # Lihat item dalam project
gh project item-create <number>        # Tambah item ke project
gh project item-edit --field <name>    # Edit field item
```

---

## 🔐 Variable & Secret (untuk Actions)

```bash
gh variable set <name>                 # Set variable untuk Actions
gh variable list                       # Lihat daftar variable
gh variable delete <name>              # Hapus variable
gh secret set <name>                   # Set secret untuk Actions
gh secret list                         # Lihat daftar secret
gh secret delete <name>                # Hapus secret
```

---

## 🏷️ Label

```bash
gh label list                          # Lihat daftar label
gh label create <nama>                 # Buat label baru
gh label edit <nama>                   # Edit label
gh label delete <nama>                 # Hapus label
```

---

## 🗄️ Cache (Actions Cache)

```bash
gh cache list                          # Lihat daftar cache Actions
gh cache delete <id>                   # Hapus cache
gh cache delete --all                  # Hapus semua cache
```

---

> Last Updated: 17-Juni-2026

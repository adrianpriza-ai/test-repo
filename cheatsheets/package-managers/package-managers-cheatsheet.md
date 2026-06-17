# Package Managers Cheatsheet

Panduan lengkap **package managers** untuk berbagai sistem operasi.

---

## 📦 apt (Debian/Ubuntu)

```bash
sudo apt update              # Update package list
sudo apt upgrade             # Upgrade packages
sudo apt install <pkg>       # Install package
sudo apt remove <pkg>        # Uninstall package
sudo apt purge <pkg>         # Uninstall + config files
sudo apt search <keyword>    # Cari package
sudo apt show <pkg>          # Info package
sudo apt list --installed    # List installed packages
sudo apt autoremove          # Remove unused dependencies
sudo apt clean               # Clean downloaded packages
sudo apt edit-sources        # Edit software sources
```

---

## 🎯 pacman (Arch/EndeavourOS)

```bash
sudo pacman -Syu             # Update & upgrade semua
sudo pacman -S <pkg>         # Install package
sudo pacman -R <pkg>         # Uninstall package
sudo pacman -Rs <pkg>        # Uninstall + dependencies
sudo pacman -Ss <keyword>    # Cari package
pacman -Qi <pkg>             # Info package (installed)
pacman -Qs <keyword>         # Search installed packages
pacman -Qe                   # List explicitly installed
pacman -Qdt                  # Orphaned packages
sudo pacman -Rns $(pacman -Qdtq)  # Remove orphans
sudo pacman -Sc              # Clean cache
```

### Yay (AUR Helper)

```bash
yay -S <pkg>                 # Install dari AUR
yay -Syu                     # Update semua (termasuk AUR)
yay -Rs <pkg>                # Remove package
yay -Ss <keyword>            # Search AUR
```

---

## 🍺 brew (macOS/Linux)

```bash
brew install <pkg>           # Install package
brew uninstall <pkg>         # Uninstall package
brew update                  # Update brew
brew upgrade                 # Upgrade packages
brew search <keyword>        # Cari package
brew info <pkg>              # Info package
brew list                    # List installed packages
brew outdated                # Check outdated packages
brew cleanup                 # Clean old versions
brew doctor                  # Check for problems
brew cask install <app>      # Install GUI app (macOS)
```

---

## 🟢 npm (Node.js)

```bash
npm init -y                  # Init project baru
npm install <pkg>            # Install package
npm install -g <pkg>         # Install global
npm uninstall <pkg>          # Uninstall package
npm update <pkg>             # Update package
npm list                     # List installed packages
npm list -g                  # List global packages
npm outdated                 # Cek package yang outdated
npm audit                    # Cek security vulnerabilities
npm audit fix                # Fix vulnerabilities otomatis
npm cache clean --force      # Clear cache
```

### npm Scripts

```bash
npm start                    # Run script 'start'
npm test                     # Run script 'test'
npm run <script>             # Run custom script
npm run build                # Run script 'build'
```

---

## 🧶 yarn (Node.js Alternative)

```bash
yarn init                    # Init project
yarn add <pkg>               # Install package
yarn add -g <pkg>            # Install global
yarn remove <pkg>            # Uninstall package
yarn upgrade                 # Update packages
yarn list                    # List packages
yarn install                 # Install all dependencies
yarn cache clean             # Clear cache
```

---

## 🐍 pip (Python)

```bash
pip install <pkg>            # Install package
pip install -r requirements.txt # Install dari file
pip uninstall <pkg>          # Uninstall package
pip list                     # List installed packages
pip freeze > requirements.txt # Export dependencies
pip show <pkg>               # Info package
pip install --upgrade <pkg>  # Upgrade package
pip search <keyword>         # Cari package (deprecated)
pip cache purge              # Clear cache
```

### Virtual Environment

```bash
python -m venv venv          # Buat virtual environment
source venv/bin/activate     # Activate (Linux/Mac)
venv\Scripts\activate        # Activate (Windows)
deactivate                   # Deactivate venv
```

---

## ☕ Maven (Java)

```bash
mvn clean                    # Clean project
mvn compile                  # Compile project
mvn test                     # Run tests
mvn package                  # Build JAR/WAR
mvn install                  # Install ke local repo
mvn dependency:tree          # Lihat dependency tree
mvn help:effective-pom       # Show effective POM
```

---

## ⚡ Gradle (Java)

```bash
./gradlew clean              # Clean project
./gradlew build              # Build project
./gradlew test               # Run tests
./gradlew dependencies       # Lihat dependencies
./gradlew tasks              # List all tasks
./gradlew projects           # List sub-projects
```

---

## 🦀 cargo (Rust)

```bash
cargo new <project>          # Buat project baru
cargo build                  # Build project
cargo run                    # Build dan run
cargo test                   # Run tests
cargo add <crate>            # Add dependency
cargo update                 # Update dependencies
cargo clean                  # Clean build artifacts
cargo publish                # Publish to crates.io
```

---

## 🎯 Quick Comparison

| Manager | Command | Description |
|---------|---------|-------------|
| apt | `sudo apt install pkg` | Install on Debian/Ubuntu |
| pacman | `sudo pacman -S pkg` | Install on Arch |
| brew | `brew install pkg` | Install on macOS/Linux |
| npm | `npm install pkg` | Install Node.js package |
| pip | `pip install pkg` | Install Python package |
| cargo | `cargo add crate` | Add Rust dependency |

---

> Last Updated: 17-Juni-2026

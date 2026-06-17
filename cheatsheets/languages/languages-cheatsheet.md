# Programming Languages Cheatsheet

Panduan lengkap untuk **Node.js**, **Python**, **Java**, dan bahasa lainnya.

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
nvm --version                # Check nvm version
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
python -m pip install <pkg>  # Install via python module
```

### Common Python Modules

```bash
python -m http.server 8000   # Start web server
python -m json.tool file.json # Format JSON
python -m py_compile file.py # Check syntax
```

---

## ☕ Java

### Maven

```bash
mvn clean                    # Clean project
mvn compile                  # Compile project
mvn test                     # Run tests
mvn package                  # Build JAR/WAR
mvn install                  # Install ke local repo
mvn dependency:tree          # Lihat dependency tree
mvn help:effective-pom       # Show effective POM
```

### Gradle

```bash
./gradlew clean              # Clean project
./gradlew build              # Build project
./gradlew test               # Run tests
./gradlew dependencies       # Lihat dependencies
./gradlew tasks              # List all tasks
./gradlew projects           # List sub-projects
```

### Java Commands

```bash
java -version                # Check Java version
javac Main.java              # Compile Java file
java Main                    # Run Java program
jar -cvf app.jar *           # Create JAR file
jar -tvf app.jar             # View JAR contents
```

---

## 🦀 Rust

### cargo (Rust Package Manager)

```bash
cargo new <project>          # Buat project baru
cargo build                  # Build project
cargo run                    # Build dan run
cargo test                   # Run tests
cargo add <crate>            # Add dependency
cargo update                 # Update dependencies
cargo clean                  # Clean build artifacts
cargo publish                # Publish to crates.io
cargo doc                    # Generate documentation
cargo fmt                    # Format code
cargo clippy                 # Lint code
```

---

## 🔷 TypeScript

### tsc (TypeScript Compiler)

```bash
tsc --init                   # Initialize tsconfig.json
tsc                          # Compile TypeScript
tsc --watch                  # Compile in watch mode
tsc --noEmit                 # Type check only
```

### ts-node (Run TypeScript directly)

```bash
ts-node file.ts              # Run TypeScript file
ts-node --transpile-only     # Skip type checking
```

---

## 💎 Ruby

### gem (Ruby Package Manager)

```bash
gem install <gem>            # Install gem
gem uninstall <gem>          # Uninstall gem
gem list                     # List installed gems
gem update                   # Update all gems
gem search <keyword>         # Search gems
```

### bundler

```bash
bundle install               # Install dependencies
bundle update                # Update dependencies
bundle exec <command>        # Run command in context
bundle outdated              # Check outdated gems
```

---

## 🐘 PHP

### Composer (PHP Package Manager)

```bash
composer init                # Initialize project
composer install             # Install dependencies
composer require <pkg>       # Add package
composer update              # Update dependencies
composer dump-autoload       # Regenerate autoload
composer show                # List installed packages
```

### PHP Commands

```bash
php -v                       # Check PHP version
php file.php                 # Run PHP script
php -S localhost:8000        # Start dev server
php -l file.php              # Syntax check
php -r "echo 'hello';"       # Run inline PHP
```

---

## 🎯 Quick Reference

| Language | Command | Description |
|----------|---------|-------------|
| Node.js | `npm install` | Install dependencies |
| Node.js | `nvm use 18` | Switch to Node 18 |
| Python | `python -m venv venv` | Create virtual env |
| Python | `pip freeze > requirements.txt` | Export deps |
| Java | `mvn clean install` | Build project |
| Java | `./gradlew build` | Build with Gradle |
| Rust | `cargo build --release` | Build optimized |
| TypeScript | `tsc --watch` | Watch mode compile |
| PHP | `composer install` | Install dependencies |

---

> Last Updated: $(date +%Y-%m-%d)

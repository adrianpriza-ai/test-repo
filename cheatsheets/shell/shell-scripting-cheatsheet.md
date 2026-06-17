# Shell Scripting Cheatsheet

Panduan lengkap **Bash scripting** untuk automasi dan command-line tasks.

---

## 📝 Basic Syntax

### Shebang

```bash
#!/bin/bash                  # Bash script
#!/bin/sh                    # POSIX shell script
```

### Variables

```bash
NAME="John"                  # Define variable
echo $NAME                   # Use variable
echo ${NAME}                 # Safer syntax
readonly PI=3.14             # Constant variable
unset NAME                   # Delete variable
```

### Special Variables

```bash
$0                           # Script name
$1, $2, ...                  # Arguments
$#                           # Number of arguments
$@                           # All arguments
$?                           # Exit code of last command
$$                           # Process ID
$!                           # Last background process PID
```

---

## 🔀 Conditionals

### If Statement

```bash
if [ condition ]; then
    echo "True"
elif [ other_condition ]; then
    echo "Also true"
else
    echo "False"
fi
```

### Test Conditions

```bash
# File tests
[ -f file ]                  # Regular file
[ -d dir ]                   # Directory
[ -e path ]                  # Exists
[ -r file ]                  # Readable
[ -w file ]                  # Writable
[ -x file ]                  # Executable
[ -s file ]                  # Not empty
[ -L file ]                  # Symbolic link

# String tests
[ -z "$str" ]                # Empty string
[ -n "$str" ]                # Not empty
[ "$a" = "$b" ]              # Equal
[ "$a" != "$b" ]             # Not equal

# Number tests
[ $a -eq $b ]                # Equal
[ $a -ne $b ]                # Not equal
[ $a -gt $b ]                # Greater than
[ $a -ge $b ]                # Greater or equal
[ $a -lt $b ]                # Less than
[ $a -le $b ]                # Less or equal
```

### Case Statement

```bash
case $variable in
    pattern1)
        command1
        ;;
    pattern2|pattern3)
        command2
        ;;
    *)
        default_command
        ;;
esac
```

---

## 🔁 Loops

### For Loop

```bash
# Basic for loop
for i in 1 2 3 4 5; do
    echo "Number $i"
done

# Range
for i in {1..5}; do
    echo "Number $i"
done

# Files
for file in *.txt; do
    echo "Processing $file"
done

# C-style
for ((i=0; i<5; i++)); do
    echo "Iteration $i"
done
```

### While Loop

```bash
counter=0
while [ $counter -lt 5 ]; do
    echo $counter
    ((counter++))
done

# Read file line by line
while IFS= read -r line; do
    echo "$line"
done < file.txt

# Infinite loop with break
while true; do
    echo "Running..."
    sleep 1
    if [ condition ]; then
        break
    fi
done
```

### Until Loop

```bash
until [ condition ]; do
    echo "Waiting..."
    sleep 1
done
```

---

## 📦 Functions

### Basic Function

```bash
greet() {
    echo "Hello $1"
}
greet "User"
```

### Function with Return

```bash
add() {
    local sum=$(($1 + $2))
    echo $sum
    return 0
}
result=$(add 5 3)
echo "Result: $result"
```

### Local Variables

```bash
my_function() {
    local var="local value"   # Only visible in function
    global_var="global value" # Visible everywhere
}
```

---

## 🎯 Useful One-Liners

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

# Extract tar.gz
tar -xzvf archive.tar.gz

# Replace text in files
find . -type f -name "*.txt" -exec sed -i 's/old/new/g' {} \;

# Kill all processes matching pattern
pkill -f "pattern"

# Watch directory for changes
watch -n 1 'ls -la'

# Parallel execution
parallel -j 4 ./script.sh ::: {1..10}
```

---

## 🛠️ Input/Output

### Reading Input

```bash
# Read from user
read -p "Enter name: " name
echo "Hello $name"

# Read with timeout
read -t 5 -p "Quick answer: " answer

# Read password (hidden)
read -sp "Password: " password
echo
```

### Output Redirection

```bash
command > file               # Overwrite output
command >> file              # Append output
command 2>&1                 # Redirect stderr to stdout
command &> file              # Redirect all output
command > /dev/null 2>&1     # Discard all output
command tee file             # Output to screen and file
```

### Command Substitution

```bash
current_date=$(date)         # Modern syntax
files=`ls`                   # Legacy syntax
echo "Today is $current_date"
```

---

## ⚡ Advanced Features

### Arrays

```bash
# Define array
fruits=("apple" "banana" "cherry")

# Access elements
echo ${fruits[0]}            # First element
echo ${fruits[@]}            # All elements
echo ${#fruits[@]}           # Array length

# Add element
fruits+=("orange")

# Iterate
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done
```

### String Manipulation

```bash
str="Hello World"

# Length
echo ${#str}                 # 11

# Substring
echo ${str:0:5}              # Hello

# Replace
echo ${str/World/Universe}   # Hello Universe

# Remove prefix/suffix
echo ${str#Hello }           # World
echo ${str% World}           # Hello

# Uppercase/Lowercase
echo ${str^^}                # HELLO WORLD
echo ${str,,}                # hello world
```

### Arithmetic

```bash
# Arithmetic expansion
result=$((5 + 3))
((result++))
((result *= 2))

# Declare integer
declare -i num=10
num=num+5
```

### Trap (Signal Handling)

```bash
cleanup() {
    echo "Cleaning up..."
    rm -f /tmp/temp_file
    exit 1
}

trap cleanup SIGINT SIGTERM

# Long running process
while true; do
    sleep 1
done
```

---

## 📋 Script Template

```bash
#!/bin/bash

set -euo pipefail            # Strict mode

# Configuration
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
LOG_FILE="/var/log/script.log"

# Functions
log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $*" | tee -a "$LOG_FILE"
}

error_exit() {
    log "ERROR: $1"
    exit 1
}

# Main
main() {
    log "Script started"
    
    # Your code here
    
    log "Script completed"
}

# Run main
main "$@"
```

---

## 🎯 Quick Reference

| Syntax | Description |
|--------|-------------|
| `#!/bin/bash` | Shebang for bash |
| `VAR=value` | Define variable |
| `$VAR` | Use variable |
| `[ condition ]` | Test condition |
| `if []; then fi` | If statement |
| `for i in list; do done` | For loop |
| `while []; do done` | While loop |
| `func() { }` | Define function |
| `$()` | Command substitution |
| `${array[@]}` | All array elements |

---

> Last Updated: $(date +%Y-%m-%d)

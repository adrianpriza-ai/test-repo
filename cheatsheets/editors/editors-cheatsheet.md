# Text Editors CLI Cheatsheet

Panduan lengkap untuk **Vim**, **Nano**, dan text editor CLI lainnya.

---

## 📝 Vim Basics

### Opening Files

```bash
vim file                     # Buka file
vim -R file                  # Buka read-only
vimdiff file1 file2          # Compare dua file
vim +10 file                 # Buka di baris 10
vim -c "search" file         # Buka dan cari text
```

### Modes

```
NORMAL mode       - Mode default (tekan ESC)
INSERT mode       - Untuk mengetik (tekan i)
VISUAL mode       - Untuk select text (tekan v)
COMMAND mode      - Untuk command (tekan :)
```

### Basic Navigation

```
h j k l          - Kiri, Bawah, Atas, Kanan
w                - Next word
b                - Previous word
0                - Beginning of line
$                - End of line
gg               - Go to first line
G                - Go to last line
:n               - Go to line n
Ctrl+f           - Page down
Ctrl+b           - Page up
```

### Insert Mode

```
i                - Insert before cursor
I                - Insert at beginning of line
a                - Append after cursor
A                - Append at end of line
o                - Open new line below
O                - Open new line above
ESC              - Exit insert mode
```

### Editing

```
x                - Delete character
dd               - Delete line
dw               - Delete word
dt'              - Delete until '
yy               - Yank (copy) line
yw               - Yank word
p                - Paste after cursor
P                - Paste before cursor
u                - Undo
Ctrl+r           - Redo
.                - Repeat last change
```

### Visual Mode

```
v                - Start visual mode
V                - Visual line mode
Ctrl+v           - Visual block mode
y                - Yank selected
d                - Delete selected
>                - Indent right
<                - Indent left
```

### Search & Replace

```
/pattern         - Search forward
?pattern         - Search backward
n                - Next match
N                - Previous match
*                - Search word under cursor
:s/old/new/g     - Replace in current line
:%s/old/new/g    - Replace in entire file
:%s/old/new/gc   - Replace with confirm
```

### Save & Quit

```
:w               - Save
:q               - Quit
:q!              - Quit without saving
:wq              - Save and quit
:x               - Save and quit (if changed)
:wa              - Save all buffers
:e file          - Edit another file
```

### Advanced Commands

```
:set nu          - Show line numbers
:set nonu        - Hide line numbers
:set hlsearch    - Highlight search results
:set nohlsearch  - Remove highlight
:set ic          - Case insensitive search
:set paste       - Paste mode
:history         - Command history
:registers       - Show registers
```

### Split Windows

```
:split           - Horizontal split
:vsplit          - Vertical split
Ctrl+w, w        - Switch window
Ctrl+w, c        - Close window
Ctrl+w, =        - Equal size windows
```

### Macros

```
qa               - Start recording macro 'a'
...commands...   - Do your commands
q                - Stop recording
@a               - Play macro 'a'
@@               - Repeat last macro
```

---

## 📄 Nano Basics

### Opening Files

```bash
nano file                    # Buka file
nano +10 file                # Buka di baris 10
nano -R file                 # Read-only mode
```

### Basic Shortcuts

```
Ctrl+O                       - Save (Write Out)
Ctrl+X                       - Exit
Ctrl+S                       - Save (quick save)
Ctrl+W                       - Search (Where Is)
Ctrl+\\                      - Replace
Ctrl+K                       - Cut line
Ctrl+U                       - Paste
Ctrl+Y                       - Page up
Ctrl+V                       - Page down
Alt+\                        - Beginning of file
Alt+/                        - End of file
Alt+6                        - Copy line
Alt+R                        - Run macro
```

### Navigation

```
Ctrl+A                       - Beginning of line
Ctrl+E                       - End of line
Ctrl+P                       - Previous line
Ctrl+N                       - Next line
Ctrl+F                       - Forward one character
Ctrl+B                       - Backward one character
```

### Command Line Options

```bash
nano -l                      # Log errors to ~/.nano-errorlog
nano -m                      # Enable mouse support
nano -B                      # Backup before saving
nano -C /path                # Custom backup directory
```

---

## 🔧 Other CLI Editors

### Emacs Basics

```bash
emacs file                   # Buka file
```

```
Ctrl+x Ctrl+s               - Save
Ctrl+x Ctrl+c               - Quit
Ctrl+x Ctrl+f               - Find file
Ctrl+s                      - Search
Ctrl+r                      - Reverse search
Ctrl+x u                    - Undo
Ctrl+/                      - Undo (alternative)
```

### Micro Editor

```bash
micro file                   # Buka file (modern nano alternative)
```

```
Ctrl+S                       - Save
Ctrl+Q                       - Quit
Ctrl+F                       - Search
Ctrl+Z                       - Undo
Ctrl+Y                       - Redo
Ctrl+C                       - Copy
Ctrl+X                       - Cut
Ctrl+V                       - Paste
```

---

## 🎯 Quick Reference

| Editor | Save | Quit | Search | Copy | Paste |
|--------|------|------|--------|------|-------|
| Vim | `:w` | `:q` | `/pattern` | `yy` | `p` |
| Nano | `Ctrl+O` | `Ctrl+X` | `Ctrl+W` | `Alt+6` | `Ctrl+U` |
| Emacs | `C-x C-s` | `C-x C-c` | `C-s` | - | - |
| Micro | `Ctrl+S` | `Ctrl+Q` | `Ctrl+F` | `Ctrl+C` | `Ctrl+V` |

---

## 💡 Tips & Tricks

### Vim Configuration (~/.vimrc)

```vim
set number              " Show line numbers
set tabstop=4           " Tab = 4 spaces
set shiftwidth=4        " Indent width
set expandtab           " Tabs to spaces
set syntax on           " Syntax highlighting
set autochdir           " Auto change directory
set ignorecase          " Case insensitive search
set smartcase           " Smart case search
```

### Nano Configuration (~/.nanorc)

```bash
include "/usr/share/nano/*.nanorc"  " Include syntax highlighting
set linenumbers                     " Show line numbers
set tabsize 4                       " Tab = 4 spaces
set softwrap                        " Soft wrap lines
```

---

> Last Updated: 17-Juni-2026

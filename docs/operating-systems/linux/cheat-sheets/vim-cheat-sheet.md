# Vim Cheat Sheet

## Overview

Vim is a powerful, highly configurable text editor available on most Linux and Unix systems. It uses different modes for editing, navigation, and command execution, making it efficient for developers and system administrators.

This cheat sheet provides a quick reference to the most commonly used Vim commands, shortcuts, and workflows.

---

# Vim Modes

| Mode | Purpose |
|------|---------|
| Normal Mode | Navigate and execute commands |
| Insert Mode | Insert and edit text |
| Visual Mode | Select text |
| Command Mode | Execute commands like save and quit |
| Replace Mode | Replace existing text |

---

# Starting Vim

Open a file:

```bash
vim filename.txt
```

Open a new file:

```bash
vim newfile.txt
```

Open multiple files:

```bash
vim file1 file2
```

Open at a specific line:

```bash
vim +25 file.txt
```

---

# Switching Modes

| Key | Action |
|-----|--------|
| `i` | Insert before cursor |
| `I` | Insert at beginning of line |
| `a` | Append after cursor |
| `A` | Append at end of line |
| `o` | Open new line below |
| `O` | Open new line above |
| `Esc` | Return to Normal mode |
| `R` | Replace mode |
| `v` | Visual mode |
| `V` | Visual line mode |
| `Ctrl + v` | Visual block mode |

---

# Saving and Exiting

| Command | Description |
|----------|-------------|
| `:w` | Save file |
| `:w filename` | Save as another file |
| `:q` | Quit |
| `:q!` | Quit without saving |
| `:wq` | Save and quit |
| `:x` | Save and exit |
| `ZZ` | Save and quit |
| `ZQ` | Quit without saving |

---

# Cursor Movement

| Key | Action |
|-----|--------|
| `h` | Left |
| `j` | Down |
| `k` | Up |
| `l` | Right |
| `0` | Beginning of line |
| `$` | End of line |
| `gg` | Beginning of file |
| `G` | End of file |
| `:25` | Go to line 25 |
| `w` | Next word |
| `b` | Previous word |
| `e` | End of word |

---

# Editing Text

Delete character:

```text
x
```

Delete line:

```text
dd
```

Delete multiple lines:

```text
5dd
```

Copy line:

```text
yy
```

Copy multiple lines:

```text
5yy
```

Paste:

```text
p
```

Paste before cursor:

```text
P
```

Undo:

```text
u
```

Redo:

```text
Ctrl + r
```

Repeat last command:

```text
.
```

---

# Search

Search forward:

```text
/search
```

Search backward:

```text
?search
```

Next match:

```text
n
```

Previous match:

```text
N
```

Clear search highlighting:

```text
:noh
```

---

# Find and Replace

Replace first occurrence:

```vim
:s/old/new/
```

Replace all in current line:

```vim
:s/old/new/g
```

Replace throughout file:

```vim
:%s/old/new/g
```

Replace with confirmation:

```vim
:%s/old/new/gc
```

---

# Visual Mode

Start character selection:

```text
v
```

Line selection:

```text
V
```

Block selection:

```text
Ctrl + v
```

Copy selected text:

```text
y
```

Delete selection:

```text
d
```

Indent selection:

```text
>
```

Unindent selection:

```text
<
```

---

# Working with Files

Open another file:

```vim
:e filename
```

Reload current file:

```vim
:e!
```

List open buffers:

```vim
:ls
```

Next buffer:

```vim
:bnext
```

Previous buffer:

```vim
:bprevious
```

Close buffer:

```vim
:bdelete
```

---

# Window Management

Horizontal split:

```vim
:split
```

Vertical split:

```vim
:vsplit
```

Move between windows:

```text
Ctrl + w
```

Close current window:

```vim
:q
```

---

# Line Operations

Go to line:

```vim
:50
```

Show line numbers:

```vim
:set number
```

Hide line numbers:

```vim
:set nonumber
```

Display relative numbers:

```vim
:set relativenumber
```

---

# Indentation

Indent line:

```text
>>
```

Unindent line:

```text
<<
```

Auto-indent:

```vim
=G
```

Indent entire file:

```vim
gg=G
```

---

# Useful Settings

Enable syntax highlighting:

```vim
:syntax on
```

Enable line numbers:

```vim
:set number
```

Enable auto-indent:

```vim
:set autoindent
```

Ignore case while searching:

```vim
:set ignorecase
```

Highlight search results:

```vim
:set hlsearch
```

---

# Common Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Esc` | Normal mode |
| `i` | Insert mode |
| `u` | Undo |
| `Ctrl + r` | Redo |
| `yy` | Copy line |
| `dd` | Delete line |
| `p` | Paste |
| `/` | Search |
| `n` | Next search result |
| `gg` | Beginning of file |
| `G` | End of file |
| `ZZ` | Save and quit |

---

# Essential Commands

```text
i
Esc
:w
:q
:wq
dd
yy
p
u
Ctrl+r
/search
n
gg
G
:set number
```

---

# Best Practices

- Stay in Normal mode unless editing text.
- Learn keyboard shortcuts to improve efficiency.
- Save your work frequently.
- Use search and replace for repetitive edits.
- Enable syntax highlighting for programming files.
- Practice navigation commands instead of relying on arrow keys.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Forgetting to exit Insert mode | Press `Esc` before commands |
| Closing without saving | Use `:wq` or `ZZ` |
| Using arrow keys constantly | Learn `h`, `j`, `k`, and `l` |
| Deleting accidentally | Use `u` to undo |
| Ignoring Visual mode | Use it for efficient text selection |

---

# Related Topics

- Vim
- Bash
- Linux Commands
- Shell
- Shell Scripting
- Text Editors
- System Administration
- File Management
# config-repository

A curated collection of configurations tailored to personal preferences across various applications and environments. As I continue to add to this repository, it serves as a hub for managing and maintaining consistency in my computing environment.

## Brew

To install all of the below in a single go:

`xargs brew install < my_brews.txt`

```txt
azure-cli
colima
eza
fzf
go
jq
node
nvm
tldr
```

## ~/.zshrc

I use [Oh My Zsh](https://ohmyz.sh/) with mostly standard settings.

```bash
# Uncomment the following line to use case-sensitive completion.
CASE_SENSITIVE="true"

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# Set up fzf key bindings and fuzzy completion
eval "$(fzf --zsh)"

# Eza (ls replacement) aliases
alias ls='eza'
alias l='eza -lbF --git'
alias ll='eza -lbGF --git'
alias llm='eza -lbGd --git --sort=modified'
alias la='eza -lbhHigUmuSa --time-style=long-iso --git --color-scale'
alias lx='eza -lbhHigUmuSa@ --time-style=long-iso --git --color-scale'

# specialty views
alias lS='eza -1'
alias lt='eza --tree --level=2'
alias l.="eza -a | grep -E '^\.'"
```

## VS Code

```json
"terminal.integrated.fontFamily": "SauceCodePro Nerd Font",
"window.zoomLevel": 0,
"workbench.sideBar.location": "right",
"editor.snippetSuggestions": "top",
"editor.minimap.enabled": false,
"editor.linkedEditing": true,
"editor.fontSize": 16,
"files.autoSave": "onFocusChange",
"editor.defaultFormatter": "esbenp.prettier-vscode",
"editor.formatOnSave": true,
"eslint.run": "onSave"
```

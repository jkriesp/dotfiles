# config-repository

A curated collection of configurations tailored to personal preferences across various applications and environments. As I continue to add to this repository, it serves as a hub for managing and maintaining consistency in my computing environment.

## Mac Specific
Activate Autohide of dock System Preferences → Dock → Autohide. Then run the following command:

`defaults write com.apple.dock autohide-delay -float 0; killall Dock`

restore to default:

`defaults delete com.apple.dock autohide-delay; killall Dock`

## Brew

Everything is listed in the [Brewfile](Brewfile). To install it all in a single go:

`brew bundle --file=Brewfile`

The casks (apps and fonts) may need admin rights, depending on the machine.

## Terminal (zsh + Oh My Zsh + Starship)

- [`.zshrc`](.zshrc) goes in `~/.zshrc`
- [`.config/starship.toml`](.config/starship.toml) goes in `~/.config/starship.toml` (Tokyo Night prompt)

Setup on a new Mac, after `brew bundle`:

```bash
# Homebrew in PATH (the .zshrc relies on $HOMEBREW_PREFIX)
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile

# Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# Oh My Zsh plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Config files
cp .zshrc ~/.zshrc
mkdir -p ~/.config ~/.nvm && cp .config/starship.toml ~/.config/starship.toml
```

Set the terminal font to **Hack Nerd Font Mono**, otherwise the prompt icons show as boxes.

## VS Code

### Settings

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

### Snippets

```json
{
  "Print to console": {
    "prefix": "cl",
    "scope": "javascript,typescript,javascriptreact",
    "body": ["console.log($1)"],
    "description": "console.log"
  },
  "reactComponent": {
    "prefix": "rfc",
    "scope": "javascript,typescript,javascriptreact",
    "body": [
      "function ${1:${TM_FILENAME_BASE}}() {",
      "\treturn (",
      "\t\t<div>",
      "\t\t\t$0",
      "\t\t</div>",
      "\t)",
      "}",
      "",
      "export default ${1:${TM_FILENAME_BASE}}",
      ""
    ],
    "description": "React component"
  },
  "importCSSModule": {
    "prefix": "csm",
    "scope": "javascript,typescript,javascriptreact",
    "body": ["import styles from './${TM_FILENAME_BASE}.module.css'"],
    "description": "Import CSS Module as `styles`"
  },
  "reactStyledComponent": {
    "prefix": "rsc",
    "scope": "javascript,typescript,javascriptreact",
    "body": [
      "import styled from 'styled-components'",
      "",
      "const Styled${TM_FILENAME_BASE} = styled.$0``",
      "",
      "function ${TM_FILENAME_BASE}() {",
      "\treturn (",
      "\t\t<Styled${TM_FILENAME_BASE}>",
      "\t\t\t${TM_FILENAME_BASE}",
      "\t\t</Styled${TM_FILENAME_BASE}>",
      "\t)",
      "}",
      "",
      "export default ${TM_FILENAME_BASE}",
      ""
    ],
    "description": "React styled component"
  }
}
```

## Dotfiles

Hi, these are my configuration files for whatever I use and would like to have across my machines.
I use [chezmoi](https://www.chezmoi.io/) to manage them across multiple and different machines safely.

## Set this thing up

If you want to have my setup, here's what you need to do:

```bash
chezmoi init --apply git@github.com:MagiHotline/dotfiles.git
```

... and you're done.

## Across Operating Systems...

Sometimes, just cloning these configurations files into another machine with a different operating systems from the original, something may break. Do not worry, because chezmoi allows the ability to create templates. For instance:

```bash
chezmoi add --template ~/.zshrc
chezmoi edit ~/.zshrc
```

In the templates, you can use Go syntax for templates. For instance:

```bash
{{ if eq .chezmoi.os "darwin" }}
# Configurazione specifica per macOS
eval "$(/opt/homebrew/bin/brew shellenv)"
{{ else if eq .chezmoi.os "linux" }}
# Configurazione Linux
export PATH="$PATH:/usr/local/bin"
{{ end }}
```

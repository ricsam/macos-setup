# macos-setup

## Programs
* iterm
* arc

## Vscode
1. Install vscode
2. Login to setup settings sync
3. Install code to path

## Settings
* Keyboard - key repeat + delay until repeat -> fast / short
* Keyboard - key repeats: `defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false`
* Trackpad - stracking speed -> fast
* Trackpad - secondary click -> click with two fingers
* Trackpad - more gestures -> swipe between pages -> swipe with three fingers

## Github
```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/github
cat ~/.ssh/github.pub | pbcopy
```

`vim ~/.ssh/config` and add

```
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  User git
  IdentityFile ~/.ssh/github
  HostName github.com
  Port 22
```

Verify with `ssh -T github.com`

## Shell
Install oh-my-zsh. Taken from [ohmyz.sh](https://ohmyz.sh/#install)
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install zsh-autosuggestions. Takend from [github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh)
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
add `zsh-autosuggestions` to the plugins in `vim ~/.zshrc` like
```bash
plugins=(
  git
  zsh-autosuggestions
)
```

Add time to the prompt. Add the following to the end of the `~/.zshrc` file:
```bash
reset-prompt-and-accept-line() {
    zle reset-prompt
    zle accept-line
}

zle -N reset-prompt-and-accept-line

bindkey '^m' reset-prompt-and-accept-line

PROMPT='${ret_status}%{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)%{$fg_bold[blue]%}%D{%H:%M:%S} % %{$reset_color%}'
```


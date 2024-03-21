# macos-setup

## Programs
* iterm
* vscode
* arc

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

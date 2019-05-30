# zpreztoカスタマイズ
  zprezto使用時はdotfilesはここで一括管理する。
  
  ## How To Setup
  
  ```
  cd ~
  git clone https://github.com/UTDoi/prezto.git
  setopt EXTENDED_GLOB
  for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
    ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
  done
```

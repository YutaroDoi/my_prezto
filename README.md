# zpreztoカスタマイズ
  zprezto使用時はzsh系の設定ファイルはここで一括管理する。
  
  ## How To Setup
  
  ```
  cd ~
  git clone https://github.com/UTDoi/dotfiles.git
  cd dotfiles
  sudo setup.sh
  cd ~
  setopt EXTENDED_GLOB
  for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
    ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
  done
```

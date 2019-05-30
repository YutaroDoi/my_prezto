# zpreztoカスタマイズ
  zprezto使用時はzsh設定ファイル系はここで一括管理する。
  
  ## How To Setup
  
  ```
  cd ~
  git clone --recursive https://github.com/UTDoi/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
  setopt EXTENDED_GLOB
  for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
    ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
  done
```

 ## How To Customize 
 
 runcoms以下のファイルを編集
 ファイルを追加した場合は
 ```
 for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
    ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
  done
 ```
 で再度更新

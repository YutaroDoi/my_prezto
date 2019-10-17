# zpreztoカスタマイズ
  zprezto使用時はzsh設定ファイル系はここで一括管理する。
  
  ## How To Setup
   1. pureをinstall (npmなどで）
   2. pecoをinstall(brewでいけるはず)
   3. 下のスクリプトを実行 
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

autoload -Uz compinit && compinit
setopt auto_list
setopt auto_menu
zstyle ‘:completion:*:default’ menu select=1
export LS_COLORS=‘di=34:ln=35:so=32:pi=33:ex=31:bd=46;34:cd=43;34:su=41;30:sg=46;30:tw=42;30:ow=43;30’
zstyle ‘:completion:*:default’ list-colors ${(s.:.)LS_COLORS}
export LANG=ja_JP.UTF-8
HISTFILE=$HOME/.zsh-history
HISTSIZE=1000000
SAVEHIST=1000000
setopt share_history
alias ll=‘ls -la’
alias doco=‘docker-compose’
alias rubofix=‘rubocop -a’
alias gyro=‘cd ~/workspace/gyro/’
alias chrome=‘/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome’
alias gyroxd=‘cd ~/Google\ Drive\ File\ Stream/共有ドライブ/GYROプロジェクト/04.システム系成果物/30.画面設計書’
alias qq=‘clear’
alias zq=‘source .zshrc’
alias deltmp=‘rm ~/workspace/tmp_file/*’
function select-history() {
  local tac
  if which tac > /dev/null; then
      tac=“tac”
  else
      tac=“tail -r”
  fi
  BUFFER=$(fc -l -n 1 | eval $tac | peco --query “$LBUFFER”)
  CURSOR=$#BUFFER
  zle -R -c
}
zle -N select-history
bindkey ‘^R’ select-history
### Added by Zplugin’s installer
source ‘/Users/1111859/.zplugin/bin/zplugin.zsh’
autoload -Uz _zplugin
(( ${+_comps} )) && _comps[zplugin]=_zplugin
### End of Zplugin’s installer chunk
zplugin light “zsh-users/zsh-completions”
zplugin ice wait”!0" atload”_zsh_autosuggest_start”
zplugin light “zsh-users/zsh-autosuggestions”
zplugin light “mafredri/zsh-async”
zplugin light “sindresorhus/pure”
zplugin light “marzocchi/zsh-notify”
zplugin ice wait’!0'; zplugin light “vintersnow/anyframe”
zplugin ice wait’!0'; zplugin light “b4b4r07/enhancd”
zplugin ice wait’!0'; zplugin light “lukechilds/zsh-nvm”
zplugin ice wait”!0" atinit”zpcompinit; zpcdreplay”
zplugin light “zsh-users/zsh-syntax-highlighting”
zplugin snippet ‘OMZ::plugins/git/git.plugin.zsh’
zplugin snippet ‘OMZ::plugins/zsh_reload/zsh_reload.plugin.zsh’
zplugin ice pick’k.sh’
zplugin light ‘supercrabtree/k’
zplugin snippet ‘OMZ::lib/completion.zsh’
zplugin snippet ‘OMZ::lib/compfix.zsh’
zplugin load zdharma/history-search-multi-word
zplugin ice compile”*.lzui” from”notabug”
zplugin load zdharma/zui
zplugin ice from”gh-r” as”program”; zplugin load junegunn/fzf-bin
zplugin ice as”program” atclone”rm -f src/auto/config.cache; ./configure” atpull”%atclone” make pick”src/vim”
zplugin light vim/vim
zplugin ice as”program” pick”$ZPFX/bin/git-*” make”PREFIX=$ZPFX”
zplugin light ‘tj/git-extras’
zplugin light ‘zdharma/fast-syntax-highlighting’
zplugin ice pick”async.zsh” src”pure.zsh”; zplugin light sindresorhus/pure
zplugin ice as”program” pick”$ZPFX/bin/git-*” make”PREFIX=$ZPFX”
zplugin light tj/git-extras
export ZSH_PLUGINS_ALIAS_TIPS_TEXT=‘alias-tips: ’
zplugin light ‘djui/alias-tips’
zplugin ice wait'1' atload’_zsh_autosuggest_start’
zplugin light ‘zsh-users/zsh-autosuggestions’
zplugin ice from’gh-r’ as’command’ mv’gotcha_* -> gotcha’
zplugin light ‘b4b4r07/gotcha’
zplugin light agnoster/agnoster-zsh-theme
zcompile ~/.zplugin/bin/zplugin.zsh

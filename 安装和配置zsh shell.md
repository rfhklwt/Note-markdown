## 1. `zsh`安装
```shell
sudo apt-get zsh
```

## 2. `oh-my-zsh`安装
```shell
sh -c "$(wget -O- https://gitee.com/shmhlsy/oh-my-zsh-install.sh/raw/master/install.sh)"
```

## 3. `Nerd-Fonts`字体安装
安装`p10k`主题前确保把`Nerd-Fonts`字体安装了，这样后面会顺利很多。

下载链接为:[Nerd-Fonts](https://www.nerdfonts.com/font-downloads)，找到`Hack Nerd Font`，下载双击安装即可。

## 4. pk10主题安装
```shell
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## 5. 插件安装

* zsh-autosuggestions
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
* zsh-syntax-highlighting
```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
* autojump
```shell
git clone git@github.com:wting/autojump.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/autojump
```
对于`autojump`，我们还需要人工安装一下，运行
```shell
cd /home/qling/.oh-my-zsh/custom/plugins/autojump
./install.py
```
打开`~/.zshrc`后修改：
```
ZSH_THEME="/powerlevel10k/powerlevel10k"

plugins=(
    git
    colored-man-pages
    colorize
    github
    brew
    osx
    docker
    docker-compose
    autojump
    zsh-autosuggestions
    zsh-syntax-highlighting
    autopep8
    python
)
```

然后运行
```
source ~/.zshrc
```
会有`p10k`引导，按照说明进行操作即可。若没出现也可输入`p10k configure`来进入引导页面。

### 一些特殊图案设置(`in .p10k.sh`)
```
  # Separator between same-color segments on the left.
  typeset -g POWERLEVEL9K_LEFT_SUBSEGMENT_SEPARATOR='\uE0C0'
  # Separator between same-color segments on the right.
  typeset -g POWERLEVEL9K_RIGHT_SUBSEGMENT_SEPARATOR='\uE0C2'
  # Separator between different-color segments on the left.
  typeset -g POWERLEVEL9K_LEFT_SEGMENT_SEPARATOR='\uE0C0'
  # Separator between different-color segments on the right.
  typeset -g POWERLEVEL9K_RIGHT_SEGMENT_SEPARATOR='\uE0C2'
  # The right end of left prompt.
  typeset -g POWERLEVEL9K_LEFT_PROMPT_LAST_SEGMENT_END_SYMBOL='\uE0C0'
  # The left end of right prompt.
  typeset -g POWERLEVEL9K_RIGHT_PROMPT_FIRST_SEGMENT_START_SYMBOL='\uE0C2'
```
### 字体设置(`in .p10k.sh`)
```
typeset -g POWERLEVEL9K_MODE="nerdfont-complete"
```
## 字体在Visual Studio Code的安装 (Optinal)
* Visual Studio Code: 

Open File → Preferences → Settings, enter `terminal.integrated.fontFamily` in the search box and set the value to `MesloLGS NF`.
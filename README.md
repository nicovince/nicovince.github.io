# Development zone
## First time setup

Install various packages and download configurations repositories:

```
sudo apt-get update && sudo apt-get install -y vim git python3-pip jq tmux virtualenvwrapper
source /usr/share/virtualenvwrapper/virtualenvwrapper.sh
mkvirtualenv default
pip install pre-commit

git clone https://nicovince@github.com/nicovince/bin.git $HOME/bin
cd $HOME/bin
pre-commit install --hook-type pre-commit --hook-type commit-msg

git clone --recurse-submodules https://nicovince@github.com/nicovince/vimrc.git $HOME/.vim
echo 'source $HOME/.vim/vimrc.vim' > $HOME/.vimrc
cd $HOME/.vim
# Install hooks
pre-commit install --hook-type pre-commit --hook-type commit-msg

# Install plugins documentations
find pack -name "doc" -exec vim -u NONE -c "helptags {}" -c q \;

# Install nvim config
mkdir -p $HOME/.config
git clone --recurse-submodules https://nicovince@github.com/nicovince/nvim.git $HOME/.config/nvim

# Install various configuration files
git clone https://nicovince@github.com/nicovince/dotfiles.git ${HOME}/.dotfiles
cd $HOME/.dotfiles
pre-commit install --hook-type pre-commit --hook-type commit-msg
./init_config.sh
```

## Fix this page
Clone website [repository](https://github.com/nicovince/nicovince.github.io):
```
git clone https://github.com/nicovince/nicovince.github.io.git
cd nicovince.github.io
```
Edit, commit and push.

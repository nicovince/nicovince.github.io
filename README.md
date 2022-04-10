# First time setup

Install various packages and download configurations repositories:

```
apt-get update && apt-get install -y vim git python3-pip python3-dbus
pip install pre-commit
pip install ruamel.yaml

git clone https://nicovince@github.com/nicovince/bin.git $HOME/bin
cd $HOME/bin
pre-commit install --hook-type pre-commit --hook-type commit-msg

git clone --recurse-submodules https://github.com/nicovince/vimrc.git $HOME/.vim
echo 'source $HOME/.vim/vimrc.vim' > $HOME/.vimrc
cd $HOME/.vim
# Install hooks
pre-commit install --hook-type pre-commit --hook-type commit-msg

# Install plugins documentations
find pack -name "doc" -exec vim -u NONE -c "helptags {}" -c q \;

git clone https://nicovince@github.com/nicovince/dotfiles.git ${HOME}/.dotfiles
cd $HOME/.dotfiles
pre-commit install --hook-type pre-commit --hook-type commit-msg
./init_config.sh
```

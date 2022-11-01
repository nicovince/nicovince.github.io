# Development zone
## First time setup

Install various packages and download configurations repositories:

```
sudo apt-get update && sudo apt-get install -y vim git python3-pip python3-dbus
pip install pre-commit
pip install ruamel.yaml
pip install virtualenvwrapper

sudo bash -c 'cat <<EOF >/etc/bash_completion.d/virtualenvwrapper
# Enable virtual env
USE_FULL=no
INSTALL_DIR="/usr/local/bin/"
if [ "\$USE_FULL" = "yes" ]; then
    if [ -f \${INSTALL_DIR}/virtualenvwrapper.sh ]; then
   . \${INSTALL_DIR}/virtualenvwrapper.sh
    fi
else
    if [ -f \${INSTALL_DIR}/virtualenvwrapper_lazy.sh ]; then
   . \${INSTALL_DIR}/virtualenvwrapper_lazy.sh
    fi
fi
EOF
'

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

git clone https://nicovince@github.com/nicovince/dotfiles.git ${HOME}/.dotfiles
cd $HOME/.dotfiles
pre-commit install --hook-type pre-commit --hook-type commit-msg
./init_config.sh
```

## Fix this page
Clone website [repository](https://github.com/nicovince/nicovince.github.io):
```
git clone https://nicovince@github.com/nicovince/nicovince.github.io.git
cd nicovince.github.io
```
Edit, commit and push.

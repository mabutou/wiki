# 群晖初始化

```text
add http://www.cphub.net
install ipkg
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
P10K
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
curl https://raw.githubusercontent.com/jesseduffield/lazydocker/master/scripts/install_update_linux.sh | bash
bash <(wget --no-check-certificate https://raw.githubusercontent.com/dofy/7th-vim/master/install.sh -O -) -i
sed -i 's/robbyrussell/powerlevel10k\/powerlevel10k/g' .zshrc
sed -i 's/plugins=(git)/plugins=(git zsh-syntax-highlighting zsh-autosuggestions)/g' .zshrc
source .zshrc
cat .bashrc >> .zshrc
pip install tldr
```

```text
https://github.com/dylanaraps/neofetch/archive/7.1.0.tar.gz
tar xvf 7.1
make install 
cp neofetch /usr/bin/
```




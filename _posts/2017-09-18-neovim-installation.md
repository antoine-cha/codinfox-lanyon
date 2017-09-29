# Intro
Nvim is asynchronous and multicore. Already enough to consider it a way to go...

# Migration from vim to nvim
Start by reading some stuff there `:help nvim-from-vim`. The following will describe the main steps :
1. Installing Neavim with python support :
```
  sudo add-apt-repository ppa:neovim-ppa/unstable
  sudo apt-get install neovim
  sudo apt-get install python-neovim # Or "pip2 install neovim"
  sudo apt-get install python3-neovim # Or "pip3 install neovim"
```
2. You will create an init file for neovim that links everything to a classic vim configuration. In `~/.config/nvim/init.vim` add the following lines :
```
  set runtimepath+=~/.vim,~/.vim/after
  set packpath+=~/.vim                
  source ~/.vimrc                     
```
3. Use [Plug](https://github.com/junegunn/vim-plug) to install packages. Get the file [plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) and copy it to `~/.vim/autoload/plug.vim`. Inside nvim, you can now use `:Plug...` commands. Check the (#usefull-plugins) section for a basic plugins setup.

4. Create the right alias by putting in your `~/.bashrc` : `alias vim=nvim`

# Usefull plugins
# Ressources
- [Interesting reddit feed](https://www.reddit.com/r/neovim/comments/5i73gf/how_to_switch_to_neovim/)
- [Cool blog article](https://jacky.wtf/weblog/moving-to-neovim/)

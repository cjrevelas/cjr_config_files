INSTALL NEOVIM AND SOME USEFUL PLUGINS
--------------------------------------
sudo apt update

sudo apt-get install neovim

sudo apt-get install python-neovim

sudo apt-get install python3-neovim

open .bashrc file and append the following:
  alias vi="nvim"
  alias vimdiff="nvim -d"

  export EDITOR="nvim"

mkdir ~/.config/nvim

nvim ~/.config/init.vim

cd ~/.config/nvim/

mkdir autoload

cd autoload

sudo apt install curl

curl https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim -o plug.vim

cd ~/.config/nvim

nvim init.vim

paste the content of the init.vim file found in this repo. The file contains:
  some essential vim commands
  gruvbox plugin
  vim-fugitive plugin
  nerdtree plugin
  ctrlp plugin
  coc plugin
  vim-airline plugin
  additional plugin options
  coc conifguration commands

inside init.vim and while in escape mode, type :PlugInstall
(if plug.vim file has been successfully created in ~/.config/nvim/autoload, autocompletion will be supported for the Plug commands)

Note:
for the coc package to work properly, you need to install node.js > 12.12
to do that install npm and the node's native package manager call 'n':

sudo apt-get install npm
npm cache clean -f
sudo npm install -g n
sudo n stable
or
sudo n latest

afterwads, check that you have indeed installed the latest stable node version by running:
node -v

type the following inside a nvim file to install some useful LSPs (language server protocols):
   :CocInstall coc-clangd (requires that clangd binary has been installed inside .local directory)
   :CocInstall coc-jason
   :CocInstall coc-cmake

for fortran lsp, do the following:
   pip install fortran language server

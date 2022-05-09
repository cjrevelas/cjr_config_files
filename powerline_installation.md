INSTALL POWERLINE WITH ITS GIT FUNCTIONALITY (https://medium.com/earlybyte/powerline-for-bash-6d3dd004f6fc)
--------------------------------------------
sudo apt install python3-pip (install pip3)

pip3 install --user powerline-status (install powerline through pip3)

append the following snippet in the .bashrc file:
  export PATH=$PATH:$HOME/.local/bin
 
  # Powerline configuration
  if [ -f $HOME/.local/lib/python3.8/site-packages/powerline/bindings/bash/powerline.sh ]; then
    $HOME/.local/bin/powerline-daemon -q
    POWERLINE_BASH_CONTINUATION=1
    POWERLINE_BASH_SELECT=1
    source $HOME/.local/lib/python3.8/site-packages/powerline/bindings/bash/powerline.sh
  fi
  
logout and log back in 

at this point powerline should work, but we need to do some more steps for the git functionality
(make sure that the FORMAT (tabs/spaces) is identical, else this will not work)

open the file: ~/.local/lib/python3.8/site-packages/powerline/config_files/colorschemes/default.json

add the following snippet after the "attached_clients" entry:
  "gitstatus":                 { "fg": "gray8",           "bg": "gray2", "attrs": [] },
  "gitstatus_branch":          { "fg": "gray8",           "bg": "gray2", "attrs": [] },
  "gitstatus_branch_clean":    { "fg": "green",           "bg": "gray2", "attrs": [] },
  "gitstatus_branch_dirty":    { "fg": "gray8",           "bg": "gray2", "attrs": [] },
  "gitstatus_branch_detached": { "fg": "mediumpurple",    "bg": "gray2", "attrs": [] },
  "gitstatus_tag":             { "fg": "darkcyan",        "bg": "gray2", "attrs": [] },
  "gitstatus_behind":          { "fg": "gray10",          "bg": "gray2", "attrs": [] },
  "gitstatus_ahead":           { "fg": "gray10",          "bg": "gray2", "attrs": [] },
  "gitstatus_staged":          { "fg": "green",           "bg": "gray2", "attrs": [] },
  "gitstatus_unmerged":        { "fg": "brightred",       "bg": "gray2", "attrs": [] },
  "gitstatus_changed":         { "fg": "mediumorange",    "bg": "gray2", "attrs": [] },
  "gitstatus_untracked":       { "fg": "brightestorange", "bg": "gray2", "attrs": [] },
  "gitstatus_stashed":         { "fg": "darkblue",        "bg": "gray2", "attrs": [] },
  "gitstatus:divider":         { "fg": "gray8",           "bg": "gray2", "attrs": [] }
  
open the file: ~/.local/lib/python3.8/site-packages/powerline/config_files/themes/shell/default.json

change the following lines from:
  "function": "powerline.segments.shell.jobnum",
  "priority": 20
to:
  "function": "powerline_gitstatus.gitstatus",
  "priority": 40
  
At this point, the git functionality should work.

Finally, we need to install some powerline fonts for the tag separators.

cd ~/Downloads

git clone https://github.com/powerline/fonts.git --depth=1 fonts

./fonts/install.sh
  
open terminal preferences -> selected profile (usually it is called "unnamed" -> custom font -> Source Code Pro for Powerline Regular

it is best to do the following steps too:
  mkdir ~/.config/powerline
  mkdir ~/.config/powerline/colorschemes   
  mkdir ~/.config/powerline/themes
  mkdir ~/.config/powerline/themes/shell
and:
  cp ~/.local/lib/python3.8/site-packages/powerline/config_files/colorschemes/default.json ~/.config/powerline/colorschemes/
  cp ~/.local/lib/python3.8/site-packages/powerline/config_files/themes/shell/default.json ~/.config/powerline/themes/shell/

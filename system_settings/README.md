# mydotfile
personal dotfile  

之前需要做一些准备工作
```sh
git init --bare $HOME/.cfg
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.bashrc
```

+ The first line creates a folder ~/.cfg which is a Git bare repository that will track our files.

+ Then we create an alias config which we will use instead of the regular git when we want to interact with our configuration repository.

+ We set a flag - local to the repository - to hide files we are not explicitly tracking yet. This is so that when you type config status and other commands later, files you are not interested in tracking will not show up as untracked.
+ Also you can add the alias definition by hand to your .bashrc or use the the fourth line provided for convenience.


After you've executed the setup any file within the $HOME folder can be versioned with normal commands, replacing git with your newly created config alias, like:

```sh
config status
config add .vimrc
config commit -m "Add vimrc"
config add .bashrc
config commit -m "Add bashrc"
config push
```
推送到git
`config push -u origin master`

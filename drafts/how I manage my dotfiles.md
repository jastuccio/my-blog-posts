# How I manage my dotfiles

  For a few years I was using [Mackup](https://github.com/lra/mackup/tree/master/doc#get-official-support-for-an-application) to manage my dotfiles. Then I found an article by Nicola Paolucci on the [Atlassian blog](https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/) explaining how to store them in a git repository. My setup and this blog post are based on that article.

```
git init --bare $HOME/.my_dotfiles

alias config='/usr/bin/git --git-dir=$HOME/.my_dotfiles/ --work-tree=$HOME'

config config --local status.showUntrackedFiles no

echo "alias config='/usr/bin/git --git-dir=$HOME/.my_dotfiles/ --work-tree=$HOME'" >> $HOME/.zshrc
```

1. create ~/.my_dotfiles as a Git bare repository to track our files.  { you can replace `.my_dotfiles` with any name you like }
2. create an alias `config` to interact with our configuration repository instead of the `git` command.
3. We set a flag `- local` to the repo. It  hides files we are not tracking yet. When you type `config status` and other commands files you are not tracking will not show as untracked.
4. Add the alias definition to .zshrc  - *you may need to use .bashrc here, but you shoud probably upgrade to zsh and prezto instead ;-)*

-----


curl -Lks http://bit.do/cfg-init | /bin/bash
After you've executed the setup any file within the $HOME folder can be versioned with normal commands, replacing git with your newly created config alias, like:

1
config status
2
config add .vimrc
3
config commit -m "Add vimrc"
4
config add .bashrc
5
config commit -m "Add bashrc"
6
config push
Install your dotfiles onto a new system (or migrate to this setup)
If you already store your configuration/dotfiles in a Git repository, on a new system you can migrate to this setup with the following steps:
Prior to the installation make sure you have committed the alias to your .bashrc or .zsh:

alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
1
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
And that your source repository ignores the folder where you'll clone it, so that you don't create weird recursion problems:

echo ".cfg" >> .gitignore
1
echo ".cfg" >> .gitignore
Now clone your dotfiles into a bare repository in a "dot" folder of your $HOME:

1
git clone --bare <git-repo-url> $HOME/.cfg
Define the alias in the current shell scope:

1
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
Checkout the actual content from the bare repository to your $HOME:

1
config checkout
The step above might fail with a message like:

1
error: The following untracked working tree files would be overwritten by checkout:
2
    .bashrc
3
    .gitignore
4
Please move or remove them before you can switch branches.
5
Aborting
This is because your $HOME folder might already have some stock configuration files which would be overwritten by Git. The solution is simple: back up the files if you care about them, remove them if you don't care. I provide you with a possible rough shortcut to move all the offending files automatically to a backup folder:

1
mkdir -p .config-backup && \
2
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
3
xargs -I{} mv {} .config-backup/{}
Re-run the check out if you had problems:

1
config checkout
Set the flag showUntrackedFiles to no on this specific (local) repository:

1
config config --local status.showUntrackedFiles no
You're done, from now on you can now type config commands to add and update your dotfiles:

1
config status
2
config add .vimrc
3
config commit -m "Add vimrc"
4
config add .bashrc
5
config commit -m "Add bashrc"
6
config push
Again as a shortcut not to have to remember all these steps on any new machine you want to setup, you can create a simple script, store it as Bitbucket snippet like I did, create a short url for it and call it like this:

1
curl -Lks http://bit.do/cfg-install | /bin/bash
For completeness this is what I ended up with (tested on many freshly minted Alpine Linux containers to test it out):

git clone --bare https://bitbucket.org/durdn/cfg.git $HOME/.cfg
function config {
   /usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME $@
}
mkdir -p .config-backup
config checkout
if [ $? = 0 ]; then
  echo "Checked out config.";
  else
    echo "Backing up pre-existing dot files.";
    config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
fi;
config checkout
config config status.showUntrackedFiles no
1 git clone --bare https://bitbucket.org/durdn/cfg.git $HOME/.cfg
2 function config {
3
   /usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME $@
4
}
5
mkdir -p .config-backup
6
config checkout
7
if [ $? = 0 ]; then
8
  echo "Checked out config.";
9
  else
10
    echo "Backing up pre-existing dot files.";
11
    config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
12
fi;
13
config checkout
14
config config status.showUntrackedFiles no
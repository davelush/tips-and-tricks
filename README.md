# Tips and Tricks
A collection of tips and tricks for developers

### Working with Multiple GitHub Accounts

~~If, like me you use your work laptop for both work & home coding you probably commit against multiple GitHub accounts. Beyond the obvious splitting repositories into different working directories for work & home you also want to commit against different sets of credentials. As soon as you google around on changing accounts you'll probably see commands such as in the initial Google hits;~~
```commandline
git config --global user.email "dave.lush@gmai.com"
git config --global user.name "davelush"
```
~~All this does though, is set your global username and email address. If you do this you'll find yourself constantly running commands to flip between account. You also don't solve the credential problem. Better is to change directory to the repository you're interested in and do the following;~~
```commandline
git config user.email "dave.lush@gmai.com"
git config user.name "davelush"
```

Use this to clean up and improve this section (enormously) https://www.keybits.net/post/automatically-use-correct-ssh-key-for-remote-git-repo/

Key thing being the git clone with a username that ties up with the ssh config

```commandline
git clone git@github.com-davelush:davelush/tips-and-tricks.git
```

In order to make this work smooth like butter, don't be lazy... Make sure you [connect to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/).

### Fixing permissions issues with Homebrew

When installing tools via homebrew on MacOs you may run into errors such as the following

```commandline
Error: An exception occurred within a child process:
  Errno::EPERM: Operation not permitted @ dir_s_mkdir - /usr/local/Cellar
``` 

Simple fix (assuming a single user MacBook) is to create and take ownership of all them beautiful Cellars

```commandline
sudo mkdir -p /usr/local/include /usr/local/lib /usr/local/opt /usr/local/sbin /usr/local/Cellar
sudo chown -R $(whoami) /usr/local/include /usr/local/lib /usr/local/opt /usr/local/sbin /usr/local/Cellar
```

Adding something to check

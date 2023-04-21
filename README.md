# Tips and Tricks
A collection of tips and tricks for developers

### Working with Multiple GitHub Accounts

If, like me you use your work laptop for both work & home coding you probably commit against multiple GitHub accounts. This can bring headache of `oops.. I accidentally committed to my personal GitHub with my work account!`. Check the commit history on this respostiry and you'll see I've been going through exactly this pain :) After a fair amount of trial, error and reading the best solution I've found is as follows;

* Use SSH for both accounts
* Use a slightly non-standard hostname on checkout to select the correct SSH key

In detail;

1. Follow this documentation to [generate a new SSH key and add it to the ssh agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). Do this for both of your accounts.
2. Follow this documentation to [add the SSH key in each of your accounts](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
3. Configure SSH to use the correct identity for the each GitHub account by editing `~/.ssh/config` as follows.
```commandline
# Default github account: work
Host github.com
   HostName github.com
   IdentityFile ~/.ssh/dave_work_private_key
   IdentitiesOnly yes
   
# Other github account: home
Host github-home
   HostName github.com
   IdentityFile ~/.ssh/dave_home_private_key
   IdentitiesOnly yes
```
7. Next time you clone a Git repo, use the SSH url and add either home or work to github.com to select the correct identity. E.g.
```commandline
git clone git@github.com-home:davelush/tips-and-tricks.git
```

8. As a final piece. In order to get the committer right file in the following in the repository's `.git/config`. (note the @github.com email address)
```
[user]
	name = davelush
	email = davelush@github.com
```

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

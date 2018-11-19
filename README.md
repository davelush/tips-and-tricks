# Tips and Tricks
A collection of tips and tricks for developers

### Working with Multiple GitHub Accounts

If, like me you use your work laptop for both work & home coding you probably commit against multiple GitHub accounts. Beyond the obvious splitting repositories into different working directories for work & home you also want to commit against different sets of credentials. As soon as you google around on changing accounts you'll probably see commands such as in the initial Google hits;
```commandline
git config --global user.email "dave.lush@gmai.com"
git config --global user.name "davelush"
```
All this does though, is set your global username and email address. If you do this you'll find yourself constantly running commands to flip between account. You also don't solve the credential problem. Better is to change directory to the repository you're interested in and do the following;
```commandline
git config user.email "dave.lush@gmai.com"
git config user.name "davelush"
```

In order to make this work smooth like butter, don't be lazy... Make sure you [connect to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/).
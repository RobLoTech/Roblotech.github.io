T## Getting Started with Git


## Creating Your Identity

In order to add files, commit changes, and push files to your repository, you first need to identify as a user executing these changes. 
To do so, simply run:
```
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
```
This will set your account's default identity by specifying your email and name.
Omit --global to set the identity only in this repository.


## Start Version Controlling

If you have a directory or project you'd like to keep track of with version control, we need to initialize it. To do so, navigate to the directory and use the `git init` command. Here are the steps:

```
cd ~/Documents/myproject
git init
```
If you already have a repo and you want to clone to your local computer, you can use the `https` link with the `git clone` command. 

Navigate to the desired directory where you want the repo to be cloned and type:
```
git clone https://github.com/myproject
```
First thing you want to do is add files to your repository. 
```
git add .


```


┌──(btron㉿kali)-[~/Documents/roblotech.github.io]
└─$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   docs/My Learning/Linux/Git/Getting Started with Git.md
        new file:   docs/My Learning/Linux/Git/index.md
        modified:   docs/My Learning/Linux/Useful Commands/Cheat Sheet.md
        new file:   docs/assets/image.png
                                                                                                                                                                             
┌──(btron㉿kali)-[~/Documents/roblotech.github.io]
└─$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   docs/My Learning/Linux/Git/Getting Started with Git.md
        new file:   docs/My Learning/Linux/Git/index.md
        modified:   docs/My Learning/Linux/Useful Commands/Cheat Sheet.md
        new file:   docs/assets/image.png
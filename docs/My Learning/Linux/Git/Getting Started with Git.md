# Getting Started with Git


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
Once you've cloned the repo, any changes you make have to be pushed to the github repo. To do so, we need to stage and push some commits. We do that with `git add`, `git commit` and `git push`.  
```
git add .                         # The '.' adds all files that've been   
                                  # created or modified.

git commit -m "<Commit Message>"  # This commits the changes from the
                                  # previous step. 

git push                          # Pushes commits to github
```

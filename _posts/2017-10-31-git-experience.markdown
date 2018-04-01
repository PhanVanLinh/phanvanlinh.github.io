---
layout: post
category: "git"
title:  "Git experience"
tags: [git]
excerpt: "git"
---


### Store password
>Password will stored forever

Step 1) `git config credential.helper store`  
Step 2) Use `git pull` or `git push ...`  
Step 3) Enter username and password  
Step 4) Username and password is already stored   

**Note**  
To update, redo step from 1 -> 4  

**Reference**  
https://stackoverflow.com/a/35942890/5381331
### Cache password
> Password will store till it's timeout. However, it will reset after we reset computer

https://help.github.com/articles/caching-your-github-password-in-git/
### My alias
```
alias gs='git status'
alias gb='git branch'
alias gc='git checkout'
alias gaa='git add --all'
alias gcam='git commit --amend'
alias gcm='git commit -m'
alias gpo='git push origin'
alias gpof='git push origin -f'
alias gpr='git pull --rebase'
```

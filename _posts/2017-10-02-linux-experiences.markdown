---
layout: post
category: "operation"
title:  "Linux Experiences"
tags: [linux]
excerpt: "operation"
---

### Make alias
http://askubuntu.com/questions/17536/how-do-i-create-a-permanent-bash-alias
- Open `gedit ~/.bashrc`
- Scroll down a litle bit then you will see some alias
- Add a new `alias`
- Run `source ~/.bashrc`
#### useful alias
```
alias cls='clear'
```

### Make link to directory
- Open gedit `~/.bashrc`
- Add an export (for example: `export folderA=~/FolderTest/FolderA/`)
- Run `source ~/.bashrc`

**Example using**: `cd $folderA`


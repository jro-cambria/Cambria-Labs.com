---
title: "Multiple Git Accounts"
tags: [git, draft]
---

# How to use Multiple Git Accounts on One System
- name_organization-1
- name_oorganization-2

## Resources
- https://www.howtogeek.com/devops/how-to-manage-multiple-git-accounts-on-one-system/
- https://medium.com/wearewaes/multiple-git-accounts-on-the-same-computer-an-easy-guide-c8d3cd1e2ba8
- https://www.techwithchay.com/posts/managing-multiple-git-accounts-on-same-computer/

## Set default user / email at the system user level
```
git config --global user.name username

git config --global user.email email
```

## Set local user / email at the repository-level
```
git config user.name username

git config user.email email
```

## Use SSH keys for Git
```
ssh-add ~/.ssh/secondary
```

To make Git use different keys for different accounts, edit ~/.ssh/config and add a Host block for each account:

!!! warning "To review & verify"

```
# Personal account (default configuration)

Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_rsa

# Work Account 1
Host github.com:secondary
 HostName github.com
 User git
 IdentityFile ~/.ssh/secondary

 # Work Account 2
Host github.com:secondary
 HostName github.com
 User git
 IdentityFile ~/.ssh/secondary
```
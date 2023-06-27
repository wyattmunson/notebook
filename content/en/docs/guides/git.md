---
title: "Git"
description: ""
lead: ""
date: 2023-06-26T21:32:16-07:00
lastmod: 2023-06-26T21:32:16-07:00
draft: false
images: []
menu:
  docs:
    parent: ""
    identifier: "git-9933cdac3bd15ebc7191dff23994b9e6"
weight: 999
toc: true
---

# Git

- [Git CLI commands](#git-cli-commands)
  - [Initial repository setup](#initial-repository-setup)
  - [Branches](#branches)
  - [Git Config](#git-config)
  - [Remotes](#remotes)
  - [Tag Commit](#tag-commit)

## Git CLI commands

```bash
# see current branch and file status
git status

# add commits to staging
git add .

# add commit message
git commit -m "fix: update date selector"

# push
git push
git push -u REMOTE_NAME BRANCH_NAME
git push -u origin main
```

## Branches

```bash
# see current branches
git branch

# See what braches are tracking upstream branches
git branch -vv
```

## Initial repository setup

```bash
git init
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:USERNAME/REPO_NAME.git
git push -u origin main
```

## Git Config

Git Config stores metadata - globally and per repository.

```bash
git config --list

git config --global user.email "your_email@example.com"

# add git config
git config --add core.sshcommand "ssh -i ~/.ssh/github"

# remove git config
git config --unset remote.github.url
```

### Remotes

Remotes refer to the location of a repository stored on an online tool like GitHub or GitLab, as opposed to the local copy stored on each user's machine. When pushing and pulling, the command is targeting a remote repository.

Most repositories push and pull from a single remote named `origin`. In more advanced use cases, multiple remotes are used for repositories stored in multiple locations.

```bash
# see remote origin
git remote show origin

# add another remote
git remote add REMOTE_NAME REMOTE_URL
git remote add origin git@github.com:USERNAME/REPO_NAME.git
git remote add second-remote git@github.com:USERNAME/REPO_NAME.git

# remove remotes
git remote remove origin
```

### Tag Commit

Tags are used to identify specific commits like a version number.

```bash
# create a tag
git tag -a v0.1.0 -m "Version 0.1.0 - do a thing"

# push tags to remote
git push --tags
```

### Pulling without pull strategy set

```
warning: Pulling without specifying how to reconcile divergent branches is
discouraged. You can squelch this message by running one of the following
commands sometime before your next pull:

  git config pull.rebase false  # merge (the default strategy)
  git config pull.rebase true   # rebase
  git config pull.ff only       # fast-forward only

You can replace "git config" with "git config --global" to set a default
preference for all repositories. You can also pass --rebase, --no-rebase,
or --ff-only on the command line to override the configured default per
invocation.
```

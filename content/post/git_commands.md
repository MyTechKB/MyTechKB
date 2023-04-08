---
title: "Git Commands"
date: 2021-12-14T21:23:08-06:00
draft: false
category: Commands
tags:
- Git
---

## Initialize global user
{{< highlight bash >}}
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
{{< / highlight >}}

## Credentials stored with in ~/.git-credentials file
{{< highlight bash >}}
git config --global credential.helper store
{{< / highlight >}}

## Git commands
{{< highlight bash >}}
# Clone repositories
git clone https://www.github.com/username/repository.git {optional dir name}
# To create a new branch
cd repository
git checkout -b feature_x
# Check status vs main
git status
# Push changes
git add .
git commit -m "message"
git push
# Or for new branch
git push origin feature_x
# Rebase branch with main
git rebase main
# Merge branch with main
git checkout master
git merge feature_x --no-ff
# Delete branch
git branch -d feature_x
# Tag new merge
git tag -a v1.3.0 -m "message"
{{< / highlight >}}

## Check if repo is ahead or behind
{{< highlight bash >}}
git fetch
# Following command lists "{local} {remote}"
git for-each-ref --format="%(refname:short) %(upstream:short)" refs/heads
# Run next command with the output of the previous command
git rev-list --left-right {local}...{remote}
# IF output contains '<', then local is ahead - perform push
# If output contains '>', then remote is ahead - perform pull
{{< / highlight >}}

## Clone submodule
{{< highlight bash >}}
git submodule init
git submodule update
{{< / highlight >}}

## Remove submodule
{{< highlight bash >}}
# Remove the submodule entry from .git/config
git submodule deinit -f path/to/submodule
# Remove the submodule directory from the superproject's .git/modules directory
rm -rf .git/modules/path/to/submodule
# Remove the entry in .gitmodules and remove the submodule directory located at path/to/submodule
git rm -f path/to/submodule
{{< / highlight >}}

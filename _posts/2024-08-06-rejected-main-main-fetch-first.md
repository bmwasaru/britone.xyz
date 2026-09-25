---
layout: post
title: "[rejected] main -&gt; main (fetch first)"
date: 2024-08-06 02:39:46
categories: ["git", "TILs"]
---

So I created a repository on Github and added a README file during the creation and I needed to push my local changes to the GitHub remote repository, I encountered this error because the history on the main branch are different between the local and remote repo



```
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/<my_username>/<repo_name>.git'
```



To solve this I tried:



```
$ git pull origin main --allow-unrelated-histories
```



Then I encountered this warning or was it an error (its yellow in colour):



```
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint: 
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint: 
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
```



```
I had to run the following:
```



```
$ git config pull.rebase false
$ git pull origin main --allow-unrelated-histories
```
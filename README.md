# Git Subtree Basics
If you hate `git submodule`, then you may want to give `git subtree` a try.

Let's say you already have a git repository with at least one commit. You can add another repository into this respository like this:

1. Specify you want to add a subtree
2. Specify the prefix local directory into which you want to pull the subtree
3. Specify the remote repository URL [*of the subtree being pulled in*]
4. Specify the remote branch [*of the subtree being pulled in*]
5. Specify you want to squash all the remote repository's [*the subtree's*] logs

`git subtree add --prefix {local directory being pulled into} {remote repo URL} {remote branch} --squash`

*For example:*

`git subtree add --prefix subtreeDirectory https://github.com/newfivefour/vimrc.git master --squash`

This will clone `https://github.com/newfivefour/vimrc.git` into the directory `subtreeDirectory`.

## Pull in new subtree commits
If you want to pull in any new commits to the subtree from the remote, issue the same command as above, replacing `add` for `pull`:

`git subtree pull --prefix subtreeDirectory https://github.com/newfivefour/vimrc.git master --squash`



## Updating / Pushing to the subtree remote repository
If you make a change to anything in `subtreeDirectory` the commit will be stored in the **host repository** and its logs. That is the biggest change from submodules.

If you now want to update the subtree remote repository with that commit, you must run the same command, excluding `--squash` and replacing `pull` for `push`.

`git subtree push --prefix subtreeDirectory https://github.com/newfivefour/vimrc.git master`

## Subtree issues

* You can't easily list the subtrees in your project
* You can't, at least easily, list the remote repositories of the subtrees
* The logs are slightly confusing when you update the host repository with subtree commits, then push the subtree to its host, and then pull the subtree.

Other than that, they're looking nicer than submodules.

*[Amended from original article](https://newfivefour.com/git-subtree-basics.html)*

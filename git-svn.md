# How to use git-svn to interact with SVN
_Shamelessly ripped from_: [My Humble Corner](https://myhumblecorner.wordpress.com/2011/08/25/git-svn-cheatsheet-for-git-rebels-in-an-svn-workplace/)

_Assumes you already know how to work with Git_

__Get a repository:__
```
$ git svn clone http://path.to.repo/svn --tags <tag/subfolder> --trunk <trunk/subfolder> --branches <branches/subfolder> 
```

__Update SVN-tracking remote branches in Git:__
```
$ git svn fetch
```

__Work on trunk:__
```
$ git checkout master
$ git svn rebase
```

__Work on branch for the very first time:__
```
$ git checkout -b local/<branchname> <remote branchname>
```

__Work on a branch:__
```
$ git checkout local/<branchname>
$ git svn rebase
```

__Push (commit) your changes to the SVN repo:__
```
$ git svn dcommit
```

__Make a new branch in SVN:__
```
# this could also be a different branch than master
$ git checkout master
$ git svn branch <branchname> -m "Branching for <reason / bug>
```

__Make a new tag in SVN:__
```
$ git checkout <tagged commit>
$ git svn tag -m "Tagging for <reason / release>
```

__Delete a branch in SVN:__
```
$ svn rm svn:://host/path/to/branch
$ git branch -D local/<branchname>
$ git branch -D -r <branchname>
$ rm -rf .git/svn/remotes/<branchname>
```

__Deleting a tag in SVN:__
```
$ svn rm svn:://host/path/to/tag
$ git branch -D -r tags/<branchname>
$ rm -rf .git/svn/refs/remotes/tags/<branchname>
```

__Merging a branch (properly):__
```
$ git checkout <merge-to branch>
$ git merge --squash <merge-from branch>
$ git commit
$ git svn dcommit
```

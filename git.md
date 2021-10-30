---
description: Git notes
---

# git



```
// status
$ git status

// list contents of staging area
$ git ls-files -s 

// list modified files
$ git ls-files -m

// interactive add ('?' to display key commands)
$ git add -p

// move staged changes back to working area
$ git reset

// move modifications to stash
$ git stash

// stash but add some context so not confused later
$ git stash save <YOUR_MESSAGE>

// list stashes (and messages)
$ git stash list

// some details of a stash
$ git stash show <STASH_ID>

// pullback in the last stash
$ git stash apply

// pullback in a specific stash
$ git stash apply <STASH_ID>

// carot means "one before" and carrot with a number means n before
// Example: the below means checkout the file from one commit prior to the 
// SHA
$ git checkout 163f833^ -- hello.template

// this means 3 commit prior
$ git checkout 163f833^3 -- hello.template
```

## Merging

```
// Keeping local feature branch up to date with master
$ git fetch origin master
$ git rebase origin/master

// merge w/ fast-forward off and will force a commit for the merge to be in 
// history 
$ git merge --no-ff <BRANCH_NAME>

// use rerere (Reuse Recorded Resolution) in current project
$ git config rerere.enabled true
```

## Printing Things

```
// list out branches
$ git branch

// print out references (options: --tags, --heads)
$ git show-ref 

// print tree of git objects (if 'tree' is installed - use brew)
$ tree .git

// print out object file contents
$ cat <PATH Example: ".git/HEAD">

// print type of object in git tree
$ git cat-file -t <SHA Example: '733a3'>

// pretty print object details
$ git cat-file -p <SHA Example: '733a3'>

// print commits (options: --reflog --oneline)
$ git log 

$ git log --graph

```

## Undoing things

```
// Undo all unstaged modifications
$ git restore .

// copy a file from the staging area (HEAD) to the working area
$ git checkout -- [PATH_TO_FILE]

// copy a file from a specific branch to the working area
$ git checkout [BRABCH SHA] -- [PATH_TO_FILE]
```

## Creating References

```
// Light weight tag
$ git tag a-tag-title

// Annotated tag
$ git tag -a "a-tag-title" -m "Some meta message with useful information"
```

## Deleting Stuff

```
// Delete a file
$ git rm [PATH_TO_FILE]
```

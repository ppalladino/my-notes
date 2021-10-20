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
```

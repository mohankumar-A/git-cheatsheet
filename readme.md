# GIT IT

*set user name and email:*

`git config --global user.name <user name>`

`git config --global user.email <email id>`

*get user name and email:*

`git config --global user.name`

`git config --global user.email`

**CORE GIT COMMANDS:**

`git init - intiate new git repo`

`git status - status of the repo`

`git add <file name>`

`git add . (add all the unstaged files)`

`git commit -m <message>`

**ATOMIC COMMITS**

When possible, a commit should encompass a single feature, change or fix.

Try to keep each commit focused on a single thing.

This makes it much easier to undo or rollback changes later on. it also makes your code or project to easy to review.

- use present tense and imperative commit message.

**GIT COMMIT**

using just (git commit without passing -m arg):

vim editor to enter commit message:

    - insert mode (i key) to start typing message
    - write commit message
    - esc
    - :wq
    - enter

nano editor to enter commit message:

    - write commit message
    - ctrl + o
    - enter
    - ctrl + x

this is useful when we need to commit message with multiple messages

we can change the editor to favorite editor.

visit below site for various editor option:
https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config

Visual Studio Code:

`git config --global core.editor "code --wait"`

**GIT LOGS:**

`git log`

    - to see the history of the commits and messages

*commit formatting args:*

    - --oneline

**BRANCHING:**

`git checkout -b <branch-name> <base-branch-name>`

`git switch -c <branch-name> <base-branch-name>`

Delete branch:

`git branch -d <branch-name>`

`git branch -D <branch-name> (force delete branch)`

**MERGING:**

1. switch to branch where you want to merge
2. `git merge <branch-name>`

**GIT DIFF:**

*unstaged diff:*

`git diff`

*working directory diff:*

`git diff HEAD`

`git diff --`

*staged changed diff:*

`git diff --staged`

`git diff --cached`

*diff specific file:*

`git diff HEAD [filename]`

`git diff --staged [filename]`

`git diff --cached [filename]`

`git diff branch1..branch2 [filename]`

`git diff commit1..commit2 [filename]`

*compare changes between two branches*

`git diff branch1..branch2`

`git diff branch1 branch2`

*compare changes between two commits*

`git diff commit1..commit2`

`git diff commit1 commit2`

`git diff HEAD HEAD~1`
(head~[num] - previous commit number)

*see changes in GUI*

git karken to view the diff files.

**GIT STASH:**

Git provide easy way of stashing these uncommitted changes so that we can return to them later, without having to making unnecessary commits.

`git stash` is super useful command that helps you to save changes that you are not yet ready to commit. You can stash changes and then come back to them later.

Running git stash will take all uncommitted changes (staged and unstaged) and stash them, reverting the changes in your working copy.

`git stash` (or) `git stash save`

use to save the changes in your stash.

`git stash pop`

use to remove the most recently stashed changes in your stash and re-apply then to your working copy.

`git stash apply`

use to apply whatever is stashed away, without removing it from the stash. this can be useful if you want to apply stashed changes to multiple branches.

**Stashing multiple times**

You can add multiple stashes onto the stack of stashes. They will all be stashed in the order you added in.

`git stash apply stash@{id}`

**Drop stashes**

`git stash drop stash@{id}`

`git stash clear`

**Undoing changes and time travelling**

- checking out commits
- escaping detached head
- discard changes with checkout
- git restore
- git reset
- git revert

`git checkout commit [commit-hash]`

`git checkout <commit-id>`

**Detached head**

While doing checkout for particular commit, head will be detached.

you can notice some suggestion from git like below

```
Note: switching to '<commit-id>'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at <commit-id> added chapter2, added user and story
```

`git log --oneline` will list upto this <commit-id> and notice the head attached to that commit id.

`git status` will display `HEAD detached at <commit-id> nothing to commit, tree clean`.

HEAD usually refers/points to a branch not a specific commit.

To goback, simply checkout will do `git checkout <branch-name>` or `git switch <branch-name>`

Options of detached head:

- Stay in detached head and examine the files, etc.
- Leave and goback to  whatever branch you were before, reattach the HEAD.
- Create new branch based on the commit and you can now save changes, since HEAD is no longer de-attached.

**Different type of checkout:**

`git checkout HEAD`
`git checkout HEAD~1`
`git checkout HEAD~2`
`git checkout HEAD~3`

`git switch -`, will move to the previous branch we were.

**Discard changes:**

`git checkout HEAD <filename>`
`git checkout -- <filename>`

*git restore:*

`git restore <filename>`
`git restore --source HEAD~1 <filename>`
`git restore --source <commithash> <filename>`

*unstaged file with git restore:*

`git restore --stage <filename>`

*undoing commit with git reset:*

`git reset <commithash>`
- will reset to commit, with current changes

`git reset --hard <commithash>`
- will reset to commit without any current changes.
- will deletes previous commits

# GIT HUB:

**cloning remote repo:**

`git clone <url>`

**SSH config:**
- checking [ssh keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)
- generating [new ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

*View git remote:*

`git remote`
`git remote -v`
`git remote add origin <url>`
`git remote rename <old url> <new url>`
`git remote remove <url>`

*Git push:*

`git push <remote> <branch>`

ex:

`git push origin master`

*Git push remote with other branch*

`git push <remote> <local-branch>:<remote-branch>`

ex:


`git push origin pancake:waffle`

*Git push origin with -u flag or up stream flag:*

`git push -u <remote> <branch-name>`
`git push -u <remote> <local-branch-name>:<remote-branch-name>`

ex:

`git push -u origin master`

after this link is made between local master and remote master and when ever we push without branch name it will automatically map upstream to remote master branch.

`git push origin`

Above will push automatically to master branch.

*Branch rename:*

`git branch -M <new-branch-name>`

above will rename current branch name to new branch name
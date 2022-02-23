# Git & GitHub

## Table of Contents
1. **[Quick Reference](#quick-reference)**
2. **[Git Commands](#git-commands)**
   - [`git init`](#git-init)
   - [`git clone`](#git-clone)
   - [`git status`](#git-status)
   - [`git add`](#git-add)
   - [`git commit`](#git-commit)
   - [`git log`](#git-log)
   - [`git diff`](#git-diff)
   - [`git remote`](#git-remote)
   - [`git push`](#git-push)
   - [`git fetch`](#git-fetch)
   - [`git merge`](#git-merge)
   - [`git pull`](#git-pull)
   - [`git branch`](#git-branch)
   - [`git checkout`](#git-checkout)
   - [`git revert`](#git-revert)
   - [`git reset`](#git-reset)
   - [`git stash`](#git-stash)
   - [`git tag`](#git-tag)
3. **[Common Use Cases](#common-use-cases)**
4. **[Text Resources](#text-resources)**
5. **[YouTube Videos](#youtube-videos)**

---
## Quick Reference:
| Command | Description |
| --- | --- |
| [`git init`](#git-init) | Initialize a new repository in the current directory |
| [`git clone`](#git-clone) | Clone a repository from another location (like GitHub) to a local directory |
| [`git status`](#git-status) | List all *new or modified* files |
| [`git add`](#git-add) | **Stage** *new or modified* files for commiting them |
| [`git commit`](#git-commit) | Commit **staged** changes to the current branch |
| [`git log`](#git-log) | Show commit logs |
| [`git diff`](#git-diff) | Show file differences that **haven't been** staged |
| [`git remote`](#git-remote) | Manage the set of repositories ("remotes") whose branches you track. |
| [`git push`](#git-push) | Send your locally commited changes to the remote |
| [`git fetch`](#git-fetch) | Download changes from the remote - Does **not** apply / merge changes |
| [`git merge`](#git-merge) | Join two or more development histories together |
| [`git pull`](#git-pull) | Fetch *and* merge changes from the remote - Fetched changes get applied directly |
| [`git branch`](#git-branch) | List, create, or delete branches |
| [`git checkout`](#git-checkout) | Switch branches or restore working tree files |
| [`git revert`](#git-revert) | Revert some existing commits |
| [`git reset`](#git-reset) | Reset current HEAD to the specified state |
| [`git stash`](#git-stash) | Stash uncommited changes from the current working directory to apply them later |
| [`git tag`](#git-tag) | Manage tags - A way to label your commits |

---
## Git Commands

### `git init`
### `git clone`
### `git status`
### `git add`
### `git commit`
### `git log`
### `git diff`
### `git remote` 2
### `git push`
### `git fetch`
### `git merge` 3
### `git pull`
### `git branch`
### `git checkout` 
### `git revert`
### `git reset`
### `git stash`
#### **Description**
Stash is a way for you to have a virtual pile of uncommited changes, which is independant from the current branch or working copy of the repo.

From the [official documentation](https://git-scm.com/docs/git-stash):

> Use `git stash` when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the `HEAD` commit.\
\
The modifications stashed away by this command can be listed with `git stash list`, inspected with `git stash show`, and restored (potentially on top of a different commit) with `git stash apply`. Calling `git stash` without any arguments is equivalent to `git stash push`. A stash is by default listed as "WIP on **branchname** …​", but you can give a more descriptive message on the command line when you create one.\
\
The latest stash you created is stored in `refs/stash`; older stashes are found in the reflog of this reference and can be named using the usual reflog syntax (e.g. `stash@{0}` is the most recently created stash, `stash@{1}` is the one before it, `stash@{2.hours.ago}` is also possible). Stashes may also be referenced by specifying just the stash index (e.g. the integer `n` is equivalent to `stash@{n}`).

#### **Example**
We are currently in the main branch of some repo and there are changes in index.html we want to stash away. After that we will restore them in another branch.

We take a look at the current status:
```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
Since we want to stash our changes, we run the following:
```
$ git stash
Saved working directory and index state WIP on main: fdade05 Initial commit
```
If we take a look at our stash, we can find our entry:
```
$ git stash list
stash@{0}: WIP on main: fdade05 Initial commit
```
Now we checkout to another branch, where we will restore our stashed changes later. For reference see [`git checkout`](#git-checkout). We take a look at our status:
```
$ git status
On branch git-stash-example
nothing to commit, working tree clean
```
We see that there are no changed files. Now we proceed to restore our changes we stashed earlier:
```
$ git stash apply
On branch git-stash-example
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
As we can see, we directly get a status on the changes we applied. We successfully brought over the changes from the main branch to another one using `git stash`. Awesome! :partying_face:

#### Further Reading:
[Official Documentation - `git stash`](https://git-scm.com/docs/git-stash)

### `git tag` 1

---
## Common Use Cases
- `git branch -m master main`
- https://stackoverflow.com/questions/520650/make-an-existing-git-branch-track-a-remote-branch
- https://stackoverflow.com/questions/6591213/how-do-i-rename-a-local-git-branch
- https://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr
- https://stackoverflow.com/questions/45096755/fatal-ambiguous-argument-origin-unknown-revision-or-path-not-in-the-working

---
## Text Resources:
- **[Git Website](https://git-scm.com)**
  - **[Git Reference](https://git-scm.com/docs) - The Official Documentation of Git**[^1]
  - [Pro Git Book](https://git-scm.com/book/en/v2)
    - [German version](https://www.git-scm.com/book/de/v2)
- **Resources from [Atlassian](https://www.atlassian.com/):**
  - [Git Cheatsheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)
  - [Beginner Tutorial](https://www.atlassian.com/git/tutorials/what-is-version-control)
    - [German version](https://www.atlassian.com/de/git/tutorials/what-is-version-control)
- **[GitHub Help Pages](https://docs.github.com/en)**

---
## YouTube Videos:
- [Git Explained in 100 Seconds](https://www.youtube.com/watch?v=hwP7WQkmECE) by [Fireship](https://www.youtube.com/channel/UCsBjURrPoezykLs9EqgamOA)
- [GitHub Pull Request in 100 Seconds - Git a FREE sticker 🔥](https://www.youtube.com/watch?v=8lGpZkjnkt4) by [Fireship](https://www.youtube.com/channel/UCsBjURrPoezykLs9EqgamOA)
- [Git It? How to use Git and Github](https://www.youtube.com/watch?v=HkdAHXoRtos) by [Fireship](https://www.youtube.com/channel/UCsBjURrPoezykLs9EqgamOA)
- [13 Advanced (but useful) Git Techniques and Shortcuts](https://www.youtube.com/watch?v=ecK3EnyGD8o) by [Fireship](https://www.youtube.com/channel/UCsBjURrPoezykLs9EqgamOA)
- [Learn Git In 15 Minutes](https://www.youtube.com/watch?v=USjZcfj8yxE) by [Colt Steele](https://www.youtube.com/channel/UCrqAGUPPMOdo0jfQ6grikZw)
- [Learn Github in 20 Minutes](https://www.youtube.com/watch?v=nhNq2kIvi9s) by [Colt Steele](https://www.youtube.com/channel/UCrqAGUPPMOdo0jfQ6grikZw)
- #### From our Workshop Git / GitHub: [1.9: Resolving Merge Conflicts - Git and GitHub for Poets](https://www.youtube.com/watch?v=JtIX3HJKwfo) by [The Coding Train](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw)
  - [Playlist containing the "**Git and GitHub for Poets**" tutorial series](https://www.youtube.com/watch?v=BCQHnlnPusY&list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) by [The Coding Train](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw)

---
[^1]: This is the main source on which the information in this page is based.
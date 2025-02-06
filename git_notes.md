# Git

## Setup

Download Git: [https://www.git-scm.com/](https://git-scm.com/)

Or included in Xcode command line tools

1. Intall git: `brew install git`
2. Verify installation: `git --version`
3. `git config --global [user.name](http://user.name/) "w3schools-test"
git config --global user.email "[test@w3schools.com](mailto:test@w3schools.com)"`
    - To set the username/email just for current repo: remove `global`
    - The user name doesn’t have to be same as GitHub. Use real name(This would appear in commit history)
4. Optional: Set VS code as default code editor for Git:
`git config --global core.editor "code --wait"`
5. Confirm configuration: `git config --list`

## Basics

**After navigating to the folder(repository)**

- initialize folder for git: `git init`
- `git status` or `git status --short`

### Choose files to ignore

`touch .gitignore`

inside created `.gitignore` file,  add `.DS_Store` (for example)

### Stage

- Stage a specific file: `git add <file-name>`
- Stage multiple specific files: `git add <file1> <file2> ...`
- Stage all changes in the current directory (including new, modified, and deleted files): `git add --all` or `git add -A`
`git add .` may not update sub-directories properly
- Stage all files of a specific type: `git add *.extension`
- Stage a file in a specific subdirectory: `git add path/to/file`
- Unstage a file (if you added it by mistake): `git reset <file-name>`

### Commit

`git commit -m "First release of Hello World!"`

- Commit without stage step: 
`git commit -a -m "Updated index.html with a new line"`

### Amend

For most recent commit

`git commit --amend -m "Added lines to [README.md](http://readme.md/)"`

### log: `git log`

Just commits: `git log --oneline`

Last commit: `git log -1` (-2: last two etc.)

Track branch pointers and HEAD: `git reflog`

### Help

• `git *command* -help` -  See all the available options for the specific command
• `git help --all` -  See all possible commands

### Branch

- New branch: `git branch hello-world-images`
- View branch: `git branch`
    - View local and remote branches: `git branch -a`
    - View remote branches: `git branch -r`
- Move to branch: `git checkout hello-world-images`
- Create and move to branch: `git checkout -b emergency-fix`
- Delete branch: `git branch -d hello-world-images`
- Force delete a branch(unmerged branch)
    
    `git branch -D feature-branch`
    
- Delete a remote branch
    
    `git push origin --delete <branch-name>`
    ex: `git push origin --delete feature-branch`
    
- Remove local reference to a remote branch
    
    `git remote prune origin`
    
    (Deleted remote branches will be still shown in terminal. This command will clean up those)
    

### Merge

Go to master brach first

- `git merge emergency-fix`
- Merge conflict
    
    conflicts will be shown on files
    
    review → edit → commit
    

Delete branch after merging

### Rebase

Ex:

```
A---B---C---D (main)
     \
      E---F---G (feature)
```

`git checkout feature`

Might need to fetch also

`git rebase origin/master` : Rebase current changes on top of origin/master

- If conflicts occur
    
    Local file will show conflicts. Fix them and `git rebase --continue`
    

```
A---B---C---D (main)
             \
              E'---F'---G' (feature)
```

- If merged instead
    
    ```
    A---B---C---D---M (main)
         \       /
          E---F---G (feature)
    ```
    

### In a view

- `q` to exit a view
- If on Vim: Press `esc` to move to command mode
    - `:wq` and Enter to write and quit
    - `:q!` and Enter to quit without saving

### After the renaming a file

`git mv <old-file-name> <new-file-name>`

## GitHub

First create a repository

`git remote add origin [https://github.com/w3schools-test/hello-world.git](https://github.com/w3schools-test/hello-world.git)`

Now on, `origin` is a shorthand for this link

- Verify connection: `git remote -v`
- Upload files on folder: `git push --set-upstream origin master`
- Push: `git push origin` (should commit first)

### Pull

- Fetch
    
    Downloads, but doesn’t merge
    
    `git fetch origin`
    
    Then check status to see if there’s any commits
    
- To see log: `git log origin/master`
- To see differences: `git diff origin/master`
- Merge: `git merge origin/master`
- Pull(=fetch+merge): `git pull origin`
    
    or just `git pull` (`pull` pulls from where upstream is set to)
    

### Pulling a branch

1. Maybe `git pull`(to check if up to date)
2. View remote branches
3. `git checkout newer-branch` (`newer branch` is a remote branch)
- When pushing, the remote `newer-branch` will be updated

### Push a new branch

1. Create a local branch (ex: `update readme`)
2. `git push origin update-readme`
- First time
    
    ```bash
    git branch -M main
    git push -u origin main
    ```
    
    - `git branch -M main`
        - Renames the default branch to main
        - By default, Git renames initial branch `master`
        - But developers and GitHub prefer `main`
    - `git push -u origin main`
        - `-u` flag sets an upstream branch for the local branch(establishes connection between local and remote branches)
        - After setting up you can just use `git push` or `git pull` instead of `git push origin main`. (Because Git now knows the link between)

### View commits that are present in local but not in upstream

`git cherry -v`

### Contribute

- Fork
    - Go to project
    - Click *Fork*
- Clone
    - Go to **original** project at GitHub
    - Click code → Copy URL
    - `git clone https://github.com/w3schools-test/w3schools-test.github.io.git *myfolder*`
- Configure remotes
    - Check how remote is set up: `git remote -v`
    - Rename origin: `git remote rename origin upstream`
    - Copy URL of our fork
    - Add that as origin: `git remote add origin [https://github.com/kaijim/w3schools-test.github.io.git](https://github.com/kaijim/w3schools-test.github.io.git)`
    
    (Recommended: Name own repository as `origin` and the one forked for as `upstream`)
    
- Push changes
    
    `git push origin`
    

## Undo/Redo

### Revert to last committed state(for saved but not staged/committed files)

- Revert to last committed state(Specific file):
 `git checkout -- file.txt`
- Discard all changes in the working directory: `git reset --hard`
- Undo changes that have been staged but not committed
    - Unstage files but keep the changes in your working directory:
    `git reset HEAD file.txt`

### Revert to specific version

1. Find the commit hash using `git log`
- Revert a specific file
    
    `git checkout a1b2c3d4 -- file.txt` (use your commit-hash)
    
- Revert entire working directory
    
    `git reset --hard a1b2c3d4`
    
- Checkout a new branch from a specific commit
    
    `git checkout -b <new-branch-name> <commit-hash>`
    
    ex: `git checkout -b new-branch a1b2c3d4`
    

### Retrieve a local branch

1. `git reflog`
2. Look for commit hash 
(ex: **`3fc9bfe** HEAD@{1}: checkout: moving from master to new-branch`)
3. `git checkout -b <branch-name> <commit-hash>`
ex: `git checkout -b recovered-branch a1b2c3d4`

---

### `git revert`: Adds a new commit (of a previous commit)

`git revert <commit_hash>`

- A→B→C: `git revert C` will create `D` that is a similar to `B`
- To Redo
    
    Just `git revert <commit_hash>` to the necessary
    
- Quickly revert to most recent commit
    
    `git revert HEAD --no-edit`
    

### `git reset` : Move back to a previous commit

ex: A → B → C → D(current working directory) (A,B,C,D : commit hashes)

1. `git reset --soft B`
    - Resets HEAD to commit B
    - C and D are staged, **not** committed(But still on current working directory)
2. `git reset --mixed B`(default)
    - Resets HEAD to commit B
    - C and D are **not** staged, not committed(But still on current working directory)
3. `git reset --hard B`
    - Resets HEAD to commit B
    - C and D are completely gone (Changes from B are on current working directory)
- Undo reset (not for `--hard` reset ones)
    
    `git reset --hard D` 
    

### `git checkout`

- `git checkout <commit_hash>`
    
    ```
    A -- B -- C (HEAD, detached)
                 \
                  D (main)
    ```
    
    Viewing commit C, but D is still there. 
    After revising is done: `git checkout main`
    
    - Use when just need to to view
        
        Because this creates a `detached HEAD` state. (Any commits will not be attached)
        
- `git checkout <commit_hash> -- file.txt`
    
    Apply a previous state of a file to current directory
    
- `git checkout -b new-branch <commit_hash>`
    
    Create a new branch from a past commit
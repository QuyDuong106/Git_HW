# Change into branch exercise 6
```
C:\Users\D U O N G\advanced-git-exercises>git checkout exercise6
Switched to a new branch 'exercise6'
branch 'exercise6' set up to track 'origin/exercise6'.
```

1. Undo changes in your working area with git checkout -- <file>
```
C:\Users\D U O N G\advanced-git-exercises>echo "bad change" > hello.template

C:\Users\D U O N G\advanced-git-exercises>type hello.template
"bad change"

C:\Users\D U O N G\advanced-git-exercises>git checkout -- hello.template

C:\Users\D U O N G\advanced-git-exercises>type hello.template
[greeting] [noun]!
This is a test of the emergency git-casting system.

C:\Users\D U O N G\advanced-git-exercises>git log --name-status --follow --oneline hello.template
4b2b90e (HEAD -> exercise6, origin/exercise6) Replacing greeting with tokens for i18n
R073    hello.txt       hello.template
fec9e7b Changing Hello to Hola
M       hello.txt
afa34a6 Changing World to Mundo
M       hello.txt
e348ebc (origin/exercise3) Testing the emergency git-casting system
M       hello.txt
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
A       hello.txt

C:\Users\D U O N G\advanced-git-exercises>git checkout fec9e7b -- hello.txt

C:\Users\D U O N G\advanced-git-exercises>type hello.txt
Hola World!
This is a test of the emergency git-casting system.

C:\Users\D U O N G\advanced-git-exercises>git reset HEAD hello.txt

C:\Users\D U O N G\advanced-git-exercises>git rm hello.template
rm 'hello.template'

C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is up to date with 'origin/exercise6'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt


C:\Users\D U O N G\advanced-git-exercises>git commit -m "Deleting hello.template"
[exercise6 e1dbf5d] Deleting hello.template
 1 file changed, 2 deletions(-)
 delete mode 100644 hello.template

C:\Users\D U O N G\advanced-git-exercises>git log --diff-filter=D --oneline -- hello.template
e1dbf5d (HEAD -> exercise6) Deleting hello.template

C:\Users\D U O N G\advanced-git-exercises>git checkout 47f11b3~1 -- hello.template
fatal: invalid reference: 47f11b3~1

C:\Users\D U O N G\advanced-git-exercises>git checkout e1dbf5d~1 -- hello.template

C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt
```

2. Clean your Repo
```
C:\Users\D U O N G\advanced-git-exercises>git clean --dry-run
Would remove hello.txt

C:\Users\D U O N G\advanced-git-exercises>git clean -f
Removing hello.txt
```

3. Git reset 
```
C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git
        hello.template

C:\Users\D U O N G\advanced-git-exercises>git reset 4b2b90e -- hello.template

C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git

C:\Users\D U O N G\advanced-git-exercises>git rm -f hello.template
rm 'hello.template'

C:\Users\D U O N G\advanced-git-exercises>type hello.template
The system cannot find the file specified.

C:\Users\D U O N G\advanced-git-exercises>git log --oneline
e1dbf5d (HEAD -> exercise6) Deleting hello.template
4b2b90e (origin/exercise6) Replacing greeting with tokens for i18n
ff91b70 (origin/exercise5) Merging in mundo branch
fec9e7b Changing Hello to Hola
4582f72 Merge branch 'exercise3' into exercise4
afa34a6 Changing World to Mundo
7ea8b01 Merge branch 'exercise3' into exercise4
e348ebc (origin/exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\D U O N G\advanced-git-exercises>git reset 4b2b90e -- hello.template
Unstaged changes after reset:
D       hello.template

C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git


C:\Users\D U O N G\advanced-git-exercises>type hello.template
The system cannot find the file specified.

```

```
C:\Users\D U O N G\advanced-git-exercises>git reset --hard HEAD
HEAD is now at e1dbf5d Deleting hello.template

C:\Users\D U O N G\advanced-git-exercises>git log -2 --oneline\
fatal: unrecognized argument: --oneline\

C:\Users\D U O N G\advanced-git-exercises>git log -2 --oneline
e1dbf5d (HEAD -> exercise6) Deleting hello.template
4b2b90e (origin/exercise6) Replacing greeting with tokens for i18n

C:\Users\D U O N G\advanced-git-exercises>git reset 4b2b90e
Unstaged changes after reset:
D       hello.template

C:\Users\D U O N G\advanced-git-exercises>git log -1 --oneline
4b2b90e (HEAD -> exercise6, origin/exercise6) Replacing greeting with tokens for i18n

C:\Users\D U O N G\advanced-git-exercises>git reset ORIG_HEAD

C:\Users\D U O N G\advanced-git-exercises>git log -1 --oneline
e1dbf5d (HEAD -> exercise6) Deleting hello.template
```

4. Git Revert
```
C:\Users\D U O N G\advanced-git-exercises>git log -1 --oneline
e1dbf5d (HEAD -> exercise6) Deleting hello.template

C:\Users\D U O N G\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git

nothing added to commit but untracked files present (use "git add" to track)

C:\Users\D U O N G\advanced-git-exercises>git revert e1dbf5d
[exercise6 9f8ce52] Revert "Deleting hello.template"
 1 file changed, 2 insertions(+)
 create mode 100644 hello.template

```
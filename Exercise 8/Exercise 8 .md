# Switch to branch master 

1. Create your own Fork
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git remote -v
origin  https://github.com/nnja/advanced-git-exercises.git (fetch)
origin  https://github.com/nnja/advanced-git-exercises.git (push) 

```

2. Set up Remotes
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git remote rename origin upstream
Renaming remote references: 100% (11/11), done.
```

3. Pull with Rebase
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git remote add origin https://github.com/QuyDuong106/Git_HW_LAB.git

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git remote -v
origin  https://github.com/QuyDuong106/Git_HW_LAB.git (fetch)
origin  https://github.com/QuyDuong106/Git_HW_LAB.git (push)
upstream        https://github.com/nnja/advanced-git-exercises.git (fetch)
upstream        https://github.com/nnja/advanced-git-exercises.git (push)

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git pull origin master --allow-unrelated-histories
remote: Enumerating objects: 31, done.
remote: Counting objects: 100% (31/31), done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 31 (delta 8), reused 2 (delta 0), pack-reused 0
Unpacking objects: 100% (31/31), 11.90 KiB | 11.00 KiB/s, done.
From https://github.com/QuyDuong106/Git_HW_LAB
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
Merge made by the 'ort' strategy.
 Exercise 1/Exercise 1.md        | 123 ++++++++++++++++++++++++
 Exercise 1/Git_HW_LAB/README.md |   2 +
 Exercise 2/Exercise 2.md        |  94 ++++++++++++++++++
 Exercise 3/Exercise 3.md        | 148 +++++++++++++++++++++++++++++
 Exercise 4/Exercise 4.md        | 206 ++++++++++++++++++++++++++++++++++++++++
 Exercise 5/Exercise 5.md        | 106 +++++++++++++++++++++
 Exercise 7/Exercise 7.md        | 103 ++++++++++++++++++++
 README.md                       |   2 +
 sample                          |   1 +
 9 files changed, 785 insertions(+)
 create mode 100644 Exercise 1/Exercise 1.md
 create mode 100644 Exercise 1/Git_HW_LAB/README.md
 create mode 100644 Exercise 2/Exercise 2.md
 create mode 100644 Exercise 3/Exercise 3.md
 create mode 100644 Exercise 4/Exercise 4.md
 create mode 100644 Exercise 5/Exercise 5.md
 create mode 100644 Exercise 7/Exercise 7.md
 create mode 100644 README.md
 create mode 160000 sample

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git branch --set-upstream-to origin/master
branch 'master' set up to track 'origin/master'.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "Change to upstream" > upstream_change.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add upstream_change.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout -b feature
Switched to a new branch 'feature'

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "change to local repo" > local_change.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add .

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m "Change to local repo"
[feature fe73753] Change to local repo
 2 files changed, 2 insertions(+)
 create mode 100644 local_change.txt
 create mode 100644 upstream_change.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git pull --rebase upstream master
From https://github.com/nnja/advanced-git-exercises
 * branch            master     -> FETCH_HEAD
Successfully rebased and updated refs/heads/feature.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
b03342f (HEAD -> feature) Change to local repo
b0704db Exercise 7 - Rebase and Amend
3cf6166 Exercise 5 - History and Diffs
4685608 Exercise 4 - Merging and rerere
68cf66a Exercise 3 - References
dedf176 Exercise 2 - Staging and Stashing
7f6eba8 Exercise 1 - Simple Command
af87584 Create README.md
5433149 initial commit
905e123 Adding another new feature
fc77e89 Master has continued to change
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, exercise4, exercise2) Initial commit
```
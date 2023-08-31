# Change into branch exercise 7 - Rebase and Amend

```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout exercise7
Switched to a new branch 'exercise7'
branch 'exercise7' set up to track 'origin/exercise7'.
```

1. Amend a Commit
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "This is the first file" > first.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "This is the second file" > second.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add first.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m"Committing two new files"
[exercise7 aac7c8d] Committing two new files
 1 file changed, 1 insertion(+)

 create mode 100644 first.txt
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit --amend
[exercise7 60d0c07] Committing two new files
 Date: Thu Aug 31 22:49:17 2023 +0700
 2 files changed, 2 insertions(+)
 create mode 100644 first.txt
 create mode 100644 second.txt
```

2. Set up for rebase
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout -b 'exercise7-2'
Switched to a new branch ''exercise7-2''

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
43388fe (HEAD -> 'exercise7-2', origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master, exercise4, exercise2) Initial commit

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "New feature" > feature.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add feature.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m"Adding new feature"
['exercise7-2' 885e143] Adding new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

 C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "Master has continued to change" >> hello.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add hello.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m "Master has continued to change"
[master fc77e89] Master has continued to change
 1 file changed, 1 insertion(+)

 C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add hello.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m "Master has continued to change"
[master fc77e89] Master has continued to change
 1 file changed, 1 insertion(+)

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout -b 'exercise7-2'
fatal: a branch named ''exercise7-2'' already exists

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git rebase master
Current branch master is up to date.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
fc77e89 (HEAD -> master) Master has continued to change
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, exercise4, exercise2) Initial commit
```

3. Interactive Rebase
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "Another new feature" > another_feature.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add another_feature.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m "Adding another new feature"
[master 905e123] Adding another new feature
 1 file changed, 1 insertion(+)
 create mode 100644 another_feature.txt

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log -n 3 --oneline
905e123 (HEAD -> master) Adding another new feature
fc77e89 Master has continued to change
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, exercise4, exercise2) Initial commit

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git rebase -i HEAD~1
Successfully rebased and updated refs/heads/master.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
905e123 (HEAD -> master) Adding another new feature
fc77e89 Master has continued to change
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, exercise4, exercise2) Initial commit
```

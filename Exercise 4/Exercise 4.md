# Change to the branch exercise 4
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout exercise4
Switched to branch 'exercise4'
Your branch is up to date with 'origin/exercise4'.

1. Fast-Forward Merge
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git merge exercise3
Updating 43388fe..e348ebc
Fast-forward
 hello.txt | 1 +
 1 file changed, 1 insertion(+)

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
e348ebc (HEAD -> exercise4, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
'''

2. Non-Fast-Forward Merge
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git status
On branch exercise4
Your branch is up to date with 'origin/exercise4'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   hello.txt


C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m "modified hello.txt"
[exercise4 8cc95e0] modified hello.txt
 1 file changed, 1 insertion(+)

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git merge --no-ff exercise3
Merge made by the 'ort' strategy.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --graph
*   commit 1a5f096f20b1f92ca73f7d286b967796a6ddbd98 (HEAD -> exercise4)
|\  Merge: 8cc95e0 e348ebc
| | Author: Quy Duong <quyduong106@gmail.com>
| | Date:   Thu Aug 31 19:04:59 2023 +0700
| |
| |     Merge branch 'exercise3' into exercise4
| |
| * commit e348ebc1187cb3b4066b1e9432a614b464bf9d07 (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3)
| | Author: Nina Zakharenko <nina@nnja.io>
| | Date:   Wed Oct 4 19:01:12 2017 -0700
| |
| |     Testing the emergency git-casting system
| |
* | commit 8cc95e0c71ca41bfeb469cc9ffa90ace59d8736d
|/  Author: Quy Duong <quyduong106@gmail.com>
|   Date:   Thu Aug 31 19:04:56 2023 +0700
|
|       modified hello.txt
|
* commit 43388fee19744e8893467331d7853a6475a227b8 (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master)
  Author: Nina Zakharenko <nina@nnja.io>
  Date:   Wed Oct 4 18:51:49 2017 -0700

      Initial commit
'''
3. Setting up for a Conflict
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git branch
  exercise2
  exercise3
* exercise4
  master

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout -b mundo
Switched to a new branch 'mundo'

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git branch
  exercise2
  exercise3
  exercise4
  master
* mundo

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git status
On branch mundo
nothing to commit, working tree clean

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>notepad hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git status
On branch mundo
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git add hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m"Changing World to Mundo"
[mundo b41cc06] Changing World to Mundo
 1 file changed, 1 insertion(+), 1 deletion(-)


 C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout exercise4
Switched to branch 'exercise4'
Your branch is ahead of 'origin/exercise4' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>notepad hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git add hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m"Changing hello to Hola"
[exercise4 8189a82] Changing hello to Hola
 1 file changed, 1 insertion(+), 1 deletion(-)

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>
'''

4. Enable ReReRe and Merge
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git config rerere.enabled true

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git merge mundo
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Recorded preimage for 'hello.txt'
Automatic merge failed; fix conflicts and then commit the result.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git rerere diff
--- a/hello.txt
+++ b/hello.txt
@@ -1,6 +1,6 @@
-<<<<<<<
-Hello Mundo!
-=======
+<<<<<<< HEAD
 Hola World!
->>>>>>>
+=======
+Hello Mundo!
+>>>>>>> mundo
 This is a test of the emergency git-casting system.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>notepad hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git rerere diff
--- a/hello.txt
+++ b/hello.txt
@@ -1,6 +1,6 @@
-<<<<<<<
-Hello Mundo!
-=======
+<<<<<<< HEAD
 Hola World!
->>>>>>>
+=======
+Hello Mundo!
+>>>>>>> mundo
 This is a test of the emergency git-casting system.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git rerere diff
--- a/hello.txt
+++ b/hello.txt
@@ -1,6 +1,6 @@
-<<<<<<<
-Hello Mundo!
-=======
+<<<<<<< HEAD
 Hola World!
->>>>>>>
+=======
+Hola Mundo!
+>>>>>>> mundo
 This is a test of the emergency git-casting system.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git add hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m "Merging in mundo branch"
Recorded preimage for 'hello.txt'
[exercise4 3286b27] Merging in mundo branch

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>
'''

5. Back up and Merge Again
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
3286b27 (HEAD -> exercise4) Merging in mundo branch
8189a82 Changing hello to Hola
b41cc06 (mundo) Changing World to Mundo
1a5f096 Merge branch 'exercise3' into exercise4
8cc95e0 modified hello.txt
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master, exercise2) Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git reset --soft HEAD~1

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
8189a82 (HEAD -> exercise4) Changing hello to Hola
1a5f096 Merge branch 'exercise3' into exercise4
8cc95e0 modified hello.txt
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master, exercise2) Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>
'''
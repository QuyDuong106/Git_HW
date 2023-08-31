# Change to branch exercise 5 - History and Diffs
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout exercise5
Switched to a new branch 'exercise5'
branch 'exercise5' set up to track 'origin/exercise5'.
'''
1. Make a Good Commit
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>notepad hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>type hello.txt
[greeting] [noun]!
This is a test of the emergency git-casting system.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git mv hello.txt hello.template

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m"Rename hello.txt to hello.template"
[exercise5 ee03dc7] Rename hello.txt to hello.template
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename hello.txt => hello.template (100%)
'''

2. Git log 
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --since="yesterday"
commit ee03dc7476c9fc6138f9847741de7c70a536da02 (HEAD -> exercise5)
Author: Quy Duong <quyduong106@gmail.com>
Date:   Thu Aug 31 19:25:58 2023 +0700

    Rename hello.txt to hello.template

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --name-status --follow --oneline hello.template
ee03dc7 (HEAD -> exercise5) Rename hello.txt to hello.template
R100    hello.txt       hello.template
fec9e7b Changing Hello to Hola
M       hello.txt
afa34a6 Changing World to Mundo
M       hello.txt
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
M       hello.txt
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master, exercise2) Initial commit
A       hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --diff-filter=R --find-renames
commit ee03dc7476c9fc6138f9847741de7c70a536da02 (HEAD -> exercise5)
Author: Quy Duong <quyduong106@gmail.com>
Date:   Thu Aug 31 19:25:58 2023 +0700

    Rename hello.txt to hello.template

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --diff-filter=M --oneline
fec9e7b Changing Hello to Hola
afa34a6 Changing World to Mundo
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
'''

3. Git show
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
ee03dc7 (HEAD -> exercise5) Rename hello.txt to hello.template
ff91b70 (origin/exercise5) Merging in mundo branch
fec9e7b Changing Hello to Hola
4582f72 Merge branch 'exercise3' into exercise4
afa34a6 Changing World to Mundo
7ea8b01 Merge branch 'exercise3' into exercise4
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master, exercise2) Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show ff91b7-
fatal: ambiguous argument 'ff91b7-': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show ff91b7
commit ff91b70c7f23de6b168dc60478f270e8e3f992a8 (origin/exercise5)
Merge: fec9e7b afa34a6
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:51:40 2017 -0700

    Merging in mundo branch

diff --cc hello.txt
index 72e64a7,3dc2209..7018e35
--- a/hello.txt
+++ b/hello.txt
@@@ -1,2 -1,2 +1,2 @@@
- Hola World!
 -Hello Mundo!
++Hola Mundo!
  This is a test of the emergency git-casting system.
'''

4. Git Branch
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git branch --merged master
  exercise2
  master

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git branch --no-merged master
  exercise3
  exercise4
* exercise5
  mundo
''' 



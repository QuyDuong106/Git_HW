'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git clone https://github.com/nnja/advanced-git-exercises.git
Cloning into 'advanced-git-exercises'...
remote: Enumerating objects: 28, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 28 (delta 0), reused 0 (delta 0), pack-reused 25
Receiving objects: 100% (28/28), done.
Resolving deltas: 100% (1/1), done.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>cd advanced-git-exercises

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout exercise3
Switched to a new branch 'exercise3'
branch 'exercise3' set up to track 'origin/exercise3'.
'''

1.  Check the value of your HEAD variable (hint: look in .git) and confirm you're pointed at the exercise3 branch.
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>type .git\HEAD
ref: refs/heads/exercise3

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git branch
* exercise3
  master

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>
'''

2. Use show-ref to look at your other heads.
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show-ref --heads
e348ebc1187cb3b4066b1e9432a614b464bf9d07 refs/heads/exercise3
43388fee19744e8893467331d7853a6475a227b8 refs/heads/master

3. Create a lightweight tag and confirm that it's pointing at the right commit.
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show-ref --heads
e348ebc1187cb3b4066b1e9432a614b464bf9d07 refs/heads/exercise3
43388fee19744e8893467331d7853a6475a227b8 refs/heads/master

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git cat-file -p 43388fee
tree 581caa0fe56cf01dc028cc0b089d364993e046b6
author Nina Zakharenko <nina@nnja.io> 1507168309 -0700
committer Nina Zakharenko <nina@nnja.io> 1507168309 -0700

Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git cat-file -p e348ebc
tree cbcdf5dda7853d595fe0b1942cb0d1d72eb910f3
parent 43388fee19744e8893467331d7853a6475a227b8
author Nina Zakharenko <nina@nnja.io> 1507168872 -0700
committer Nina Zakharenko <nina@nnja.io> 1507168872 -0700

Testing the emergency git-casting system

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git tag my-exercise3-tag

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show-ref --tags
e348ebc1187cb3b4066b1e9432a614b464bf9d07 refs/tags/my-exercise3-tag

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>tag --points-at e348ebc
'tag' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git tag --points-at e348ebc
my-exercise3-tag
'''

4. Create an annotated tag, and use git show to see more information about it.
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git tag -a "exercise3-annotated-tag" -m "This is my annotated tag for exercise 3"

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show exercise3-annotated-tqag
fatal: ambiguous argument 'exercise3-annotated-tqag': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git show exercise3-annotated-tag
tag exercise3-annotated-tag
Tagger: Quy Duong <quyduong106@gmail.com>
Date:   Thu Aug 31 18:38:33 2023 +0700

This is my annotated tag for exercise 3

commit e348ebc1187cb3b4066b1e9432a614b464bf9d07 (HEAD -> exercise3, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3)
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:01:12 2017 -0700

    Testing the emergency git-casting system

diff --git a/hello.txt b/hello.txt
index 980a0d5..b31a35b 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,2 @@
 Hello World!
+This is a test of the emergency git-casting system.
'''

5. Get into a "detached HEAD" state by checking out a specific commit, then confirm that your HEAD is pointing at this commit rather than at a branch
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
e348ebc (HEAD -> exercise3, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git checkout e348ebc
Note: switching to 'e348ebc'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at e348ebc Testing the emergency git-casting system
'''

6. Create a Dangling Commit
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>echo "This is a test file"> dangle.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git add dangle.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>commit -m"This is dangling commit"
'commit' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git commit -m"This is dangling commit"
[detached HEAD 60faab0] This is dangling commit
 1 file changed, 1 insertion(+)
 create mode 100644 dangle.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>git log --oneline
60faab0 (HEAD) This is dangling commit
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample\advanced-git-exercises>type .git\HEAD
60faab0599a7131f089bf5aeab03d6660c45d66d
'''
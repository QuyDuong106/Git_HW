1. Use git ls-files -s to view the contents of the staging area.
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git ls-files -s
100644 c7331ad9b37b60b1af245efc50f0c5cf0af77fc5 0       hello.txt
'''

2. Make a change and try to stage it interactively (git add -p).
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git add -p
No changes.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>echo "This is a test of emergency git-casting system." >> hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git add -p
diff --git a/hello.txt b/hello.txt
index c7331ad..d4f0f36 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1,2 +1,3 @@
 'Hello World!'
 "This is a test of emergency git-casting system."
+"This is a test of emergency git-casting system."
(1/1) Stage this hunk [y,n,q,a,d,e,?]? Y
<stdin>:8: trailing whitespace.
"This is a test of emergency git-casting system."
warning: 1 line adds whitespace errors.

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git ls-files -s
100644 d4f0f3685d67aa2aee1f9d42b7330fa0e476d14c 0       hello.txt
''' 

3. Unstage your Change
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git ls-files -s
100644 d4f0f3685d67aa2aee1f9d42b7330fa0e476d14c 0       hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   hello.txt


C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git ls-files -s
100644 d4f0f3685d67aa2aee1f9d42b7330fa0e476d14c 0       hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git reset hello.txt
Unstaged changes after reset:
M       hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
'''

4. Stash your changes
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git stash save "emergency git-casting"
Saved working directory and index state On master: emergency git-casting

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git status
On branch master
nothing to commit, working tree clean

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git stash list
stash@{0}: On master: emergency git-casting

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git stash show stash@{0}
 hello.txt | 2 ++
 1 file changed, 2 insertions(+)

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git stash apply stash@{0}
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

C:\Users\Asus\Desktop\NEU\LAB - GIT\advanced git\projects\sample>git diff hello.txt
diff --git a/hello.txt b/hello.txt
index d38752e..d4f0f36 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,3 @@
 'Hello World!'
+"This is a test of emergency git-casting system."
+"This is a test of emergency git-casting system."
''' 
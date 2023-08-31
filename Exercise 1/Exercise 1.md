1. Create a new folder and initialize it as a git repo
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT>cd  "C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1"

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1> mkdir projects\sample

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1>cd projects\sample

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git init
Initialized empty Git repository in C:/Users/Asus/Desktop/NEU/LAB - GIT/Exercise1/projects/sample/.git/
''' 

2. Create file, stage it, and commit it to new repo 
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>echo 'Hello World!' > hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git add hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git commit -m"Initial commit"
[master (root-commit) 36b6bdd] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 hello.txt
'''

3. Look at your git folder , using tree if you have it 
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>tree .git /A /F
Folder PATH listing
Volume serial number is 0000007E F493:FE96
C:\USERS\ASUS\DESKTOP\NEU\LAB - GIT\EXERCISE1\PROJECTS\SAMPLE\.GIT
|   COMMIT_EDITMSG
|   config
|   description
|   HEAD
|   index
|
+---hooks
|       applypatch-msg.sample
|       commit-msg.sample
|       fsmonitor-watchman.sample
|       post-update.sample
|       pre-applypatch.sample
|       pre-commit.sample
|       pre-merge-commit.sample
|       pre-push.sample
|       pre-rebase.sample
|       pre-receive.sample
|       prepare-commit-msg.sample
|       push-to-checkout.sample
|       update.sample
|
+---info
|       exclude
|
+---logs
|   |   HEAD
|   |
|   \---refs
|       \---heads
|               master
|
+---objects
|   +---10
|   |       86f661aad7332d7e343cc49afc46f942c00dfd
|   |
|   +---36
|   |       b6bdd5a06f38ba7f6cd0424531b012a57872e4
|   |
|   +---d3
|   |       8752edff821f8f38fe3efbe3d80e0ae997f5b1
|   |
|   +---info
|   \---pack
\---refs
    +---heads
    |       master
    |
    \---tags
'''

4. Inspect the objects in your .git/objects folder using git cat-file. See if you can find the tree, blob, and commit objects for your recent commit.
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -t 1086f
tree

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -p 1086f
100644 blob d38752edff821f8f38fe3efbe3d80e0ae997f5b1    hello.txt

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -t 36b6b
commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -p 36b6b
tree 1086f661aad7332d7e343cc49afc46f942c00dfd
author Quy Duong <quyduong106@gmail.com> 1693476742 +0700
committer Quy Duong <quyduong106@gmail.com> 1693476742 +0700

Initial commit

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -t d38752
blob

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git cat-file -p d38752
'Hello World!'
'''

5. Look at your .git/HEAD and .git/refs/heads/master files and see if you can figure out where these references are pointing to.
'''
C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>type .git\HEAD
ref: refs/heads/master

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>type .git\refs\heads\master
36b6bdd5a06f38ba7f6cd0424531b012a57872e4

C:\Users\Asus\Desktop\NEU\LAB - GIT\Exercise1\projects\sample>git log --oneline
36b6bdd (HEAD -> master) Initial commit
'''
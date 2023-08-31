# Switch to branch 9
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout exercise9
Switched to a new branch 'exercise9'
branch 'exercise9' set up to track 'upstream/exercise9'.
```

1. Grepping with Git
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep -e "Python"
python_code.py:# This is a Python file
python_code.py:    print("Welcome to Python!")

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep --line-number --heading --break -e "Python"
python_code.py
1:# This is a Python file
4:    print("Welcome to Python!")

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "More Python code" >> python_code.py

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep --line-number -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")
python_code.py:5:"More Python code"

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add python_code.py

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")
python_code.py:5:"More Python code"
```

2. Cherry Picking 
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
88f6e28 (HEAD -> exercise9, upstream/exercise9) Adding bash, python, and java code examples
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, exercise4, exercise2) Initial commit

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log exercise3 --oneline
e348ebc (upstream/exercise3, exercise3) Testing the emergency git-casting system
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, exercise4, exercise2) Initial commit

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git stash
Saved working directory and index state WIP on exercise9: 88f6e28 Adding bash, python, and java code examples

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git cherry-pick e348ebc
[exercise9 ca46aab] Testing the emergency git-casting system
 Author: Nina Zakharenko <nina@nnja.io>
 Date: Wed Oct 4 19:01:12 2017 -0700
 1 file changed, 1 insertion(+)
```

3. Git Blame
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git blame hello.txt
^43388fe (Nina Zakharenko 2017-10-04 18:51:49 -0700 1) Hello World!
ca46aabb (Nina Zakharenko 2017-10-04 19:01:12 -0700 2) This is a test of the emergency git-casting system.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git rm java_code.java
rm 'java_code.java'

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m "Who uses Java anyway?"
[exercise9 7c9872b] Who uses Java anyway?
 1 file changed, 7 deletions(-)
 delete mode 100644 java_code.java

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --diff-filter=D -- java_code.java
commit 7c9872b56a2f56f1d52c29e03c3fd8f27aefa11c (HEAD -> exercise9)
Author: quyduong <quyduong106@gmail.com>
Date:   Thu Aug 31 23:42:33 2023 +0700

    Who uses Java anyway?

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git blame 7c9872b56a2f56f1d52c29e03c3fd8f27aefa11c -- java_code.java
fatal: no such path java_code.java in 7c9872b56a2f56f1d52c29e03c3fd8f27aefa11c

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git blame 7c9872b56a2f56f1d52c29e03c3fd8f27aefa11c~1 -- java_code.java
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 1) // This is a Java file
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 2)
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 3) public class HelloWorld {
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 4)    public static void main(String[] args) {
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 5)       System.out.println("Привет от Java!");
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 6)    }
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 7) }
```

4. Git Bisect
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git log --oneline
7c9872b (HEAD -> exercise9) Who uses Java anyway?
ca46aab Testing the emergency git-casting system
88f6e28 (upstream/exercise9) Adding bash, python, and java code examples
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, exercise4, exercise2) Initial commit

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git bisect start 7c9872b 43388fe
Bisecting: 0 revisions left to test after this (roughly 1 step)
[ca46aabbde65fe39ece661a0ff4670c62e06a593] Testing the emergency git-casting system

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>type hello.txt
Hello World!
This is a test of the emergency git-casting system.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git bisect bad
Bisecting: 0 revisions left to test after this (roughly 0 steps)
[88f6e2864bd0829c71654f1d19096f436a66ce07] Adding bash, python, and java code examples

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>type hello.txt
Hello World!

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git bisect good
ca46aabbde65fe39ece661a0ff4670c62e06a593 is the first bad commit
commit ca46aabbde65fe39ece661a0ff4670c62e06a593
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:01:12 2017 -0700

    Testing the emergency git-casting system

 hello.txt | 1 +
 1 file changed, 1 insertion(+)
```
# Switch to branch exercise10 
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git checkout exercise10
Previous HEAD position was 88f6e28 Adding bash, python, and java code examples
Switched to a new branch 'exercise10'
branch 'exercise10' set up to track 'upstream/exercise10'.
```
1. Set up a Pre-commit Hook 
```
C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>copy pre-commit .git\hooks\pre-commit
        1 file(s) copied.

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>icacls .git/hooks/pre-commit
.git/hooks/pre-commit NT AUTHORITY\SYSTEM:(I)(F)
                      BUILTIN\Administrators:(I)(F)
                      DESKTOP-O2UGO7D\D U O N G:(I)(F)

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo "Bad bash script" > test_script.sh

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add test_script.sh

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git commit -m"Adding new test script
No shebang found! Not allowed to commit!

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>echo '#!/bin/bash\n Good bash script' > test_script.sh

C:\Users\D U O N G\Desktop\DSLab\GIT\advanced-git-exercises>git add test_script.sh


```
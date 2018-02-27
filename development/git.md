# Git

[Git](https://git-scm.com) is a [*d*istributed *v*ersion *c*ontrol *s*ystem (DVCS)](https://en.wikipedia.org/wiki/Distributed_version_control).

## Github

[Github](https://github.com) is a hosting platform for projects that use the Git version control software.

### Push an existing project to Github

 1. Create the repository on [Github](https://github.com/new).
 2. Change into the project directory.
 3. Make sure the local project is clean:
    ```
    git status
    ```
 4. add github as remote (use the URL of the repository created in step 1):
    ```
    git remote add origin https://github.com/<github-user>/<project-name>.git
    ```` 
 5. push to github:
    ```
    git push -u origin master
    ```
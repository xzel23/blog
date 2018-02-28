# Git

[Git](https://git-scm.com) is a [distributed version control system (DVCS)](https://en.wikipedia.org/wiki/Distributed_version_control).

## Common Tasks

- Change the remote URL for branch `origin`:
    ```
    git remote set-url origin <new-remote-url>
    ```

## Github

[Github](https://github.com) is a hosting platform for projects that use the Git version control software.

### How to push an existing project to Github
 
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

## Jitpack
[Jitpack](https://jitpack.io) is an easy to use package repository for Git.

Simply add dependencies to your github hosted project, and Jitpack will do a build and supply the artifacts as a Maven repository.

**Bugs of interest:**
 - [Java 9 support](https://github.com/jitpack/jitpack.io/issues/1592)
 - [JavaFX is not supported Java 9 builds](https://github.com/jitpack/jitpack.io/issues/2310)

## Gitlab
[Gitlab](https://www.gitlab.com) is similar to Github in many ways. It supports private repositories and also offers CI (Continuous Integration).

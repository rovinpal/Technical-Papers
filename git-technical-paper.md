# Git – Quick Guide


## What is Version Control?

* Tracks changes in code/files.
* Lets you revert to older versions.
* Helps teams work together.
* Allows branches for features, then merge to main branch.
* Popular VCS: GitHub, GitLab, Beanstalk, PerForce


## What is Git?

* Git = free, open-source distributed version control system.
* Tracks changes, lets you undo mistakes, and see history.
* Key Concepts
  * Repository (repo): folder with code and commits.
  * Commit: save a set of changes, tracked by unique SHA1 hash.
  * Branch: separate line of development. Main branch = master or main.
  * Working directory → Staging area → Local repo → Commit


## Setting Up Git

### Check Git installed:
* git --version

### Install on Ubuntu/Linux:
* sudo apt update
* sudo apt install git

### Set name & email:
* git config --global user.name "Your Name"
* git config --global user.email "youremail@domain.com"
* git config --list


# Basic Workflow

### Initialize repo:
* git init

### Add file:
* git add a.txt

### Commit changes:
* git commit -m "message"

### Create branch:
* git branch leaf
* git checkout leaf

### Merge branch:
* git checkout master
* git merge leaf


## Good Practices
* Use .gitignore to ignore files (logs, secrets).
* Make small commits.
* Commit often, after micro-tasks.
* Commit working code only.
* Use diff tool to check changes before commit.
* Test changes before commit.
* Never commit passwords/API keys/secrets.


## Undo Changes
* Wrong commit message → git commit --amend
* Skip file in last commit → git add file && git commit --amend
* Commit on wrong branch → git reset, git cherry-pick
* Undo last N commits → git reset --hard HEAD~N
* Undo changes to file → git checkout -- file

## References
* https://www.youtube.com/watch?v=RGOj5yH7evk
* https://www.digitalocean.com/community/tutorials/how-to-contribute-to-open-source-getting-started-with-git
* https://www.youtube.com/watch?v=e2IbNHi4uCI
* https://www.freecodecamp.org/news/gitignore-what-is-it-and-how-to-add-to-repo/
* https://chris.beams.io/posts/git-commit/
* https://ohshitgit.com/

# Cheatsheet
# Cheatsheet 1: Git Basics

## Table of Contents

- [Cheatsheet](#cheatsheet)
- [Cheatsheet 1: Git Basics](#cheatsheet-1-git-basics)
  - [Table of Contents](#table-of-contents)
  - [**1. Terminology**](#1-terminology)
  - [**2. Using Git**](#2-using-git)
    - [**2.1. Creating a Repository**](#21-creating-a-repository)
    - [**2.2. Working on the Project**](#22-working-on-the-project)
    - [**2.3. Making Changes**](#23-making-changes)
    - [**2.4. Applying Changes to the `main` Branch**](#24-applying-changes-to-the-main-branch)
    - [**2.5. Downloading Changes from Remote Repository (GitHub)**](#25-downloading-changes-from-remote-repository-github)
  - [**3. Commands**](#3-commands)
    - [**3.1. Status**](#31-status)
    - [**3.2. Stashing**](#32-stashing)
    - [**3.3. Commiting**](#33-commiting)
    - [**3.4. Pushing and Pulling**](#34-pushing-and-pulling)
    - [**3.5. Branching**](#35-branching)
      - [**3.5.1. General**](#351-general)
      - [**3.5.2. Checkout**](#352-checkout)
      - [**3.5.3. Creating a Branch**](#353-creating-a-branch)
    - [**3.6. Gitk**](#36-gitk)

## **1. Terminology**
- `git` - Tool for Source Version Control
- `GitHub` - A platform for storing code (git repositories)
- `Local repository` - A repository located on the PC
- `Remote repository` - A repository located on the *GitHub*
- `Pull Request (PR)` - Request to merge two branches (on remote repository i.e. *GitHub*)

## **2. Using Git**

### **2.1. Creating a Repository**
1. Create repository on GitHub
2. Clone repository to PC
   - `git clone <repo-url>`

### **2.2. Working on the Project**
1. The git repository is initialized with `main` or `master` branch
2. Create a development branch `development` or `dev`
   - `git checkout -b development`

### **2.3. Making Changes**
1. Make changes to local repository
2. Stash changes
   - `git add .`
3. Repeat steps 1-2
4. Commit stashed changes and write a comment
   - `git commit -m "<comment>"`
5. Repeat steps 1-4
6. Push
   - `git push`

### **2.4. Applying Changes to the `main` Branch**
1. On GitHub, create a *Pull Request* from `development` to `main` branch
   - Set `pkaselj` as reviewer
   - **Do not merge before `pkaselj` approves the PR**
2. Wait for `pkaselj`'s approval
3. If **APPROVED**, go ahead and merge the PR
4. If **REJECTED**, fix errors/comments as described in [`Making Changes`](#making-changes)

### **2.5. Downloading Changes from Remote Repository (GitHub)**
1. After merging a *Pull Request*, the changes are visible only in remote repository (*GitHub*)
2. To "download" changes from `GitHub` to local repository on PC, first checkout the `main` branch and then *pull* the changes
    - `git checkout main`
    - `git pull`

## **3. Commands**

### **3.1. Status**

- `git status` - shows *uncommited* changes

### **3.2. Stashing**

- `git stash <file1> <file2> ... <fileN>` - stash files: `file1 file2 ... file N`
  - e.g. `git stash README.md main.cs`
- `git stash <directory1> <directory2> ... <directoryN>` - stash whole directories
  - e.g. `git stash include/ source/`
- `git stash .` - stash all changes

### **3.3. Commiting**

- `git commit -m "<comment>"` - Create a commit from *stashed* files and directories
  - `git commit -m "Added a new button for deleting users"`

### **3.4. Pushing and Pulling**
- `git push` - Push all *committed* changes from local repository (PC) to remote repository (*GitHub*)
- `git pull` - Pull all commits from remote repository (*GitHub*) to local repository (PC)

### **3.5. Branching**

#### **3.5.1. General**
- `git branch` - Get name of the *current* branch
- `git branch -l` - List all branches
- `git branch -d <branch>` - Delete `<branch>`
  - `git branch -d development` - Delete `development` branch 

#### **3.5.2. Checkout**
- `git checkout <branch>` - Switch to a `<branch>`
  - `git checkout main`
  - `git checkout development`
- `git checkout <commit>`
- `git checkout <tag>`

#### **3.5.3. Creating a Branch**
- `git branch <branch>` - Creates a branch named `<branch>` **but doesn't switch to that (new) branch**
- `git checkout -b <branch>` - Creates a branch named `<branch>` **and immediately switches to that (new) branch**
  - Equivalent to `git branch <branch> && git checkout <branch>`

### **3.6. Gitk**

- `gitk` - Show history of the current branch
- `gitk --all` - Show history of all branches

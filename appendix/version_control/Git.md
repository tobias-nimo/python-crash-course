# Appendix D - Using Git for Version Control

Version control software allows you to take snapshots of a project whenever it's in a working state.

When you make changes to a project—for example, when you implement a new feature—you can revert back to a previous working state if the project's current state isn't functioning well.

---

## Installing Git

### Installing Git on Windows

You can download an installer for Git at https://git-scm.com/.

### Configuring Git

Git keeps track of who makes changes to a project. To do this, Git needs to know your username and email. Open a Git CMD and enter the following:

```bash
git config --global user.name tnimo
git config --global user.email tobiasnimo99@gmail.com
```

---

## Making a Project

Let's make a project to work with. Create a folder somewhere on your system called `git_practice`. Inside the folder, make a simple Python program:

```python
print("Hello Git world!")
```

We'll use this program to explore Git's basic functionality.

---

## Ignoring Files

Files with the extension `.pyc` are automatically generated from `.py` files, so we don't need Git to keep track of them. These files are stored in a directory called `__pycache__`.

To tell Git to ignore this directory, make a special file called `.gitignore` and add the following line to it:

```
__pycache__/
```

This file tells Git to ignore any file in the `__pycache__` directory.

---

## Initializing a Repository

Now that you have a directory containing a Python file and a `.gitignore` file, you can initialize a Git repository.

Open a terminal, navigate to the `git_practice` folder, and run the following command:

```bash
git init
```

The output shows that Git has initialized an empty repository in `git_practice`. A repository is the set of files in a program that Git is actively tracking.

---

## Checking the Status

Before doing anything else, let's look at the project's status:

```bash
git status
```

Output:
```
On branch master
No commits yet
Untracked files:
    (use "git add <file>..." to include in what will be committed)
    .gitignore
    hello_git.py
nothing added to commit but untracked files present (use "git add" to track)
```

---

## Adding Files to the Repository

Let's add the two files to the repository, and check the status again:

```bash
git add .
git status
```

Output:
```
On branch master
No commits yet
Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
    new file: .gitignore
    new file: hello_git.py
```

The command `git add .` adds all files within a project that aren't already being tracked to the repository.

When we check the status of the project now, we can see that Git recognizes some changes that need to be committed.

---

## Making a Commit

Let's make the first commit:

```bash
git commit -m "Started project."
```

Output:
```
[master (root-commit) ee76419] Started project.
2 files changed, 4 insertions(+)
create mode 100644 .gitignore
create mode 100644 hello_git.py
```

```bash
git status
```

Output:
```
On branch master
nothing to commit, working tree clean
```

We issue the command `git commit -m "message"` to take a snapshot of the project.

---

## Checking the Log

Git keeps a log of all commits made to the project. Let's check the log:

```bash
git log
```

Output:
```
commit a9d74d87f1aa3b8f5b2688cb586eac1a908cfc7f (HEAD -> master)
Author: tnimo <tobiasnimo99@gmail.com>
Date: Mon Jan 21 21:24:28 2019 -0900
Started project.
```

Git provides an option to print a simpler version of the log entries:

```bash
git log --pretty=oneline
```

Output:
```
ee76419954379819f3f2cacafd15103ea900ecb2 (HEAD -> master) Started project.
```

---

## The Second Commit

To see the real power of version control, we need to make a change to the project and commit that change. Here we'll just add another line to `hello_git.py`:

```python
print("Hello Git world!")
print("Hello everyone.")
```

When we check the status of the project, we'll see that Git has noticed the file that changed:

```bash
git status
```

Output:
```
On branch master
Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)
modified: hello_git.py
no changes added to commit (use "git add" and/or "git commit -a")
```

Let's commit the change and check the status and the log again:

```bash
git commit -am "Extended greeting."
```

Output:
```
[master 51f0fe5] Extended greeting.
1 file changed, 1 insertion(+), 1 deletion(-)
```

```bash
git status
```

Output:
```
On branch master
nothing to commit, working tree clean
```

```bash
git log --pretty=oneline
```

Output:
```
51f0fe5884e045b91c12c5449fabf4ad0eef8e5d (HEAD -> master) Extended greeting.
ee76419954379819f3f2cacafd15103ea900ecb2 Started project.
```

> **Note:** If you create any new files between commits, simply reissue the `git add .` command to include the new files in the repository.

---

## Reverting a Change

Now let's look at how to abandon a change and revert back to the previous working state. First, add a new line to `hello_git.py`:

```python
print("Hello Git world!")
print("Hello everyone.")
print("Oh no, I broke the project!")
```

Save and run this file. We check the status and see that Git notices this change:

```bash
git status
```

Output:
```
On branch master
Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)
modified: hello_git.py
no changes added to commit (use "git add" and/or "git commit -a")
```

Git sees that we modified `hello_git.py`, and we can commit the change if we want to. But this time, instead of committing the change, we'll revert back to the last commit when we knew our project was working:

```bash
git checkout .
git status
```

Output:
```
On branch master
nothing to commit, working tree clean
```

> **Important:** The command `git checkout .` abandons any changes made since the last commit and restores the project to the last committed state!

> **Note:** You might have to refresh the file in your editor to see the previous version.

---

## Checking Out Previous Commits

You can check out any commit in your log, not just the most recent, by including the first six characters of the reference ID instead of a dot.

By checking out and reviewing an earlier commit, you can:

### 1. Return to the latest commit

```bash
git log --pretty=oneline
```

Output:
```
51f0fe5884e045b91c12c5449fabf4ad0eef8e5d (HEAD -> master) Extended greeting.
ee76419954379819f3f2cacafd15103ea900ecb2 Started project.
```

```bash
git checkout ee7641
```

Output:
```
Note: checking out 'ee7641'.
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:
git checkout -b <new-branch-name>
HEAD is now at ee7641... Started project.
```

When you check out a previous commit, you leave the master branch and enter what Git refers to as a **detached HEAD** state.

To get back to the master branch, you check it out:

```bash
git checkout master
```

Output:
```
Previous HEAD position was ee76419 Started project.
Switched to branch 'master'
```

### 2. Abandon recent work and pick up development from an earlier commit

If you want to discard all of the more recent commits and go back to a previous state, you can reset the project to a previous commit. From the master branch enter:

```bash
git status
```

Output:
```
On branch master
nothing to commit, working directory clean
```

```bash
git log --pretty=oneline
```

Output:
```
51f0fe5884e045b91c12c5449fabf4ad0eef8e5d (HEAD -> master) Extended greeting.
ee76419954379819f3f2cacafd15103ea900ecb2 Started project.
```

```bash
git reset --hard ee76419
```

Output:
```
HEAD is now at ee76419 Started project.
```

```bash
git status
```

Output:
```
On branch master
nothing to commit, working directory clean
```

```bash
git log --pretty=oneline
```

Output:
```
ee76419954379819f3f2cacafd15103ea900ecb2 (HEAD -> master) Started project.
```

---

## Deleting the Repository

Sometimes you'll mess up your repository's history and won't know how to recover it. If this happens, first consider asking for help using the methods discussed in Appendix C.

If you can't fix it and you're working on a solo project, you can continue working with the files but get rid of the project's history by deleting the `.git` directory. This won't affect the current state of any of the files, but it will delete all commits, so you won't be able to check out any other states of the project.

To do this, either open a file browser and delete the `.git` repository or delete it from the command line. Afterwards, you'll need to start over with a fresh repository to start tracking your changes again.

```bash
git status
```

Output:
```
On branch master
nothing to commit, working directory clean
```

```bash
rm -rf .git
git status
```

Output:
```
fatal: Not a git repository (or any of the parent directories): .git
```

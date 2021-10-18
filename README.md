# GitTuto
small notes about the most basic Git commands


# Configuration

One needs to configure Git before being able to use a repository
```
git config --global user.name "John Snow"
git config --global user.email johndsnow@example.com
```
Color for git commands output

```
git config --global color.ui true
```
Listing the global configuration

```
git config --list
```

# Starting a new  local project



Git is composed of 3 parts. Together they form the local repository. Those parts are

* **Working directory:** It correspond to the project's folder
* **Stage/Index** sits in between the working directory and the repository. Its represents all modified files that we want to appear in our future version.
* **Repository** Final local place we new version are stored.


These 3 parts are in in the local computer. To start,we got in the project folder and initialize git:
```
git init
```

Once a file is created/modified, in order to create a new version of the project, one need to add in the stagging. 

```
git add index.htlm
```

Now that we have file in the stagging, we can create a new version wiht `commit`:

```
git commit index.htm -m " New file created and added"
```

the -m is here to add a message about the commit. It should be a clear text saying what has been modified.

After the commit, we can send the project on a remote repository with the command ```git push```. First we have specify the remote repository

```
git remote add origin https://github.com/khanr1/GitTuto.git
```

with this command we have linked the local repository with the remote one. One can now send the commits to the remote repository

```
git push -u origin main
```
# Starting from a remote project

As always with start by creating a folder and initialize the project with the ```git init``` command. We then copy the URL of the remote repository we want to work on.  We then link the remote and local repository with the following command:

```
git remote add NAME
https://github.com/XXXX/YYYY.git
```

NAME represents an alias to be use later the call the repository. NAME can be what we want. Then once can simply pull the project from the remote repository to the local repository.

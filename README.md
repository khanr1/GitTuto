# GitTuto
small notes about the most basic Git commands


# Configuration

One needs to register before being able to use a repository
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



Git is composed of 3 parts. Together they form the local repository those part are

* **Working directory:** It correspond to the project's folder
* **Stage/Index** sits in between the working directory and the repository. Its represents all modified files that we want to appear in our future version.
* **Repository** Final local place we new version are stored.


These 3 parts are in in the local computer. To start,we got in the project folder and initialize git:
```
git init
```

Once a file is created/modified, in order to create a new version of the project, one need to add in the stagging. 

```
git add fichier.text
```

Now that we have file in the stagging, we can create a new version wiht `commit`:

```
git commit fichier.text -m " New file created and added"
```

the -m is here to add a message about the commit. It should be a clear text saying what has been modified.

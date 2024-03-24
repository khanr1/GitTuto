# GitTuto

These a my personal small notes about the most basic Git commands and configuration.

## Connecting to Github with SSH

To establish a secure connection with GitHub using SSH, you need to generate SSH keys using the ssh-keygen command. This process creates a private key (which should never be shared) and a corresponding public key.

By default, Linux and Mac systems have ssh-keygen installed. To generate SSH keys, open a terminal and enter:

```
ssh-keygen 
```

The private key will be stored in the file id_rsa, while the public key will be stored in id_rsa.pub.

After generating the keys, you need to register the public key with GitHub. This can be done in the GitHub settings. To conveniently copy the public key to the clipboard, you can use the following command:

```
pbcopy < ~/.ssh/id_rsa.pub
```

This command copies the contents of the id_rsa.pub file to the clipboard, allowing you to easily paste it into the appropriate field in GitHub's settings.



## Configuration

One needs to configure Git before being able to use a repository

```
git config --global user.name "John Snow"
git config --global user.email johnsnow@example.com
```
Color for git commands output

```
git config --global color.ui true
```
Listing the global configuration

```
git config --list
```

## Starting a new  local project



Git is composed of 3 parts. Together they form the local repository. Those parts are

* **Working directory:** It correspond to the project's folder
* **Stage/Index** sits in between the working directory and the repository. Its represents all modified files that we want to appear in our future version.
* **Repository** Final local place where new versions are stored.


These three parts reside on the local computer. To start, navigate to the project folder and initialize Git:
```
git init
```


Once a file is created/modified, in order to create a new version of the project, one needs to add it to the staging area:


```
git add index.htlm
```

Now that we have files in the staging area, we can create a new version with `commit`:


```
git commit index.htm -m " New file created and added"
```

After the commit, we can send the project to a remote repository with the command `git push`. But first, we need to specify the remote repository:

### How to Create a Remote Repository on GitHub and Get Its URL

1. **Sign in to GitHub:**
   Go to [GitHub](https://github.com/) and sign in to your account. If you don't have an account, you'll need to create one.

2. **Create a New Repository:**
   Once signed in, click on the "+" icon in the upper-right corner of the page and select "New repository" from the dropdown menu.

3. **Fill in Repository Details:**
   - Enter a name for your repository in the "Repository name" field.
   - Optionally, add a description to briefly explain what your project is about.
   - Choose whether the repository should be public (visible to everyone) or private (accessible only to you and selected collaborators).
   - You can also choose to initialize the repository with a README file, which is a good practice for starting a new project.

4. **Create the Repository:**
   Click on the "Create repository" button to finalize the creation of your new repository.

5. **Copy the Repository URL:**
   After the repository is created, GitHub will display a page with instructions on how to set up your local repository to push to the remote. Look for the section titled "Quick setup" or "…or push an existing repository from the command line." There, you'll find the URL of your repository, which you can copy by clicking on the clipboard icon next to it.

Now you have successfully created a remote repository on GitHub and obtained its URL. You can use this URL when specifying the remote repository in your local Git repository using the `git remote add origin <remote_URL>` command.

```
git remote add origin https://github.com/khanr1/GitTuto.git
```

with this command we have linked the local repository with the remote one. One can now send the commits to the remote repository

```
git push -u origin main
```
## Starting from a remote project

As always with start by creating a folder and initialize the project with the ```git init``` command. We then copy the URL of the remote repository we want to work on.  We then link the remote and local repository with the following command:

```
git remote add NAME
https://github.com/XXXX/YYYY.git
```

NAME represents an alias to be used later to call the repository. NAME can be whatever we want. Then one can simply pull the project from the remote repository to the local repository.

```
git pull OC main
```

## Branching

* In order to list all the branches: ``` git branch```
* In order to create a new branch : ``` git branch NewBranch```
* To go to the new branch : ``` git checkout NewBranch```

One can continue working in the branch and commit and push normally as described previously.

One can merge also the branch with the main branch to do so first  switch to the main branch ``` git checkout main``` and then merge with ```git merge NewBranch```.

## Correcting mistakes on a local repository

### creating a branch by mistake

If one creates a branch by mistake:

```
git branch -d branchName```
```

### Removing modification from the main branch

It can happen that we add a modification in the main branch while we wanted those modification to be in an other branch. If no commit has been made one can use the command 

``` git stash ```

after that we move to the branch we want the modification and type the command:

``` 
git stash apply
```

this command will apply the last stashed modification to the branch. If for some reason on has many  modifications stashed one needs to list them:

``` 
git stash list
```

and  select the one that we want to apply to the branch

``` 
git stash apply stash@{x}
```

where x is the stash id number.

### Removing a commit from  the main branch

first we need the id of the commit using 

``` git log```

then we remove the last commit

``` 
git reset --hard HEAD^
```

then we go to the branch were we wanted to do the commit and type

```git reset --hard ca83a6df```

where ca83a6df are the 8 first character of the commit id 

### Correcting the message of a commit

```
git commit --amend -m "the message"
```
### Adding a file to a commit

```
git add FichierOublie.txt 
git commit --amend --no-edit
```

with the --no-edit no need to edit the message of the commit.


# Correcting mistakes on a remote repository

If one has pushed a files with mistakes on the remote repository, one can revert the push with

```
git revert ^HEAD"
```

# Git reset



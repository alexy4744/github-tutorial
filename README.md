# GitHub Tutorial by Alex

---
## Git vs. GitHub

Git allows for version control of your files. It allows you to save snapshots (commits) of your files throughout different file changes. Git does not depend on GitHub.

GitHub, on the other hand, is a remote repository. It ***requires*** Git (unless you want to upload files manually). GitHub allows you to create remote repositories, where you can use Git to push your commits to a remote repository. Because it is a remote repository, it allows for collaboration with multiple people.

---
## Setting up your local repository

To setup Git locally, `cd` into your folder and type `git init`, assuming you already have Git installed

```bash
git init
```

To verify whether Git has been successfully initialized in the correct directory, you can use `ls -a` to view all files/folders

```bash
ls -a
```

You should see a hidden folder called `.git` in your working directory.

This means that Git has sucessfully set up your local repository

---
## Creating your remote repository.

If you do not have a GitHub account, create one [**here**](https://github.com/join?source=header-home)

After that, you can click [**here**](https://github.com/alexy4744?tab=repositories) to view all your repositories *(or click on your avatar and click "Your Repositories" in the dropdown)*.

You should see a green button called **New** on the upper right side of your screen.
<!-- put new button screenshot here -->

Now enter your repository name, it should match the name of your local repository. Then click on "Create Repository".

Now, you have both your local and remote repositories created.

---
## Connecting your local and remote repository
For every new remote and local repository created, we need to establish a connection between them in order to push commits to your remote from the local.

**There are 2 ways of establishing a connection.**
1. **SSH**
    * In order to establish a SSH connection with between our local and remote, we first need to get a SSH key from our IDE.

    * Each IDE varies, but in order to get one from Cloud9, we can go [**here**](https://c9.io/account/ssh) and copy the first public SSH key for public repositories, or the second one for private repositories.
    
    * We can then add the SSH key into our GitHub account  [**here**](https://github.com/settings/ssh/new), then add a title and paste the key in, then click on "**Add SSH Key**".
   
    * Now go back to your repository and copy the SSH url.

2. **HTTPS**
    * ***Note: HTTPS requires you to sign in to GitHub, unless you have some sort of credential manager that allows Git to save and remember your credentials.***
    
    * In order to get the HTTPS url for your repository, simply copy the HTTPS url.

After we have copied the URL (HTTPS or SSH) for our remote repository, we can go back in to our terminal, and `cd` into our working directory if you are already not in it.

To tell Git to connect to a remote, type `git remote add origin <URL>`, where \<URL> is the URL you copied...

To check if our connection has been successfully added, type `git remote -v`, where the `-v` flag means *verbose*, which will show all of our remotes.

Git should output something similar to this:
* **SSH**
  ```bash
  origin  git@github.com:<USERNAME>/<REPOSITORY NAME>.git (fetch)
  origin  git@github.com:<USERNAME>/<REPOSITORY NAME>.git (push)
  ```
* **HTTPS**
  ```bash
  origin  https://github.com/<USERNAME>/<REPOSITORY NAME>.git (fetch)
  origin  https://github.com/<USERNAME>/<REPOSITORY NAME>.git (push)
  ```

---
## Workflow & Commands

Once we have edited our files and want to push to our remote repository, here are the following commands you can follow.

1. **Adding/removing files to the stage.**

    The staging area is basically where you can prepare what files should be committed or not. You can add or remove file(s) from the stage.
   
    To view the current files that are on the stage, type `git status`. If files have been modified and not been added on to the stage, it will show `modified: FILENAME.md` in red.
   
    To add specific file(s) onto the stage, type `git add FILENAME.md`. This will add one single file onto the stage. You can attach more file names after the first one to add multiple specfic files.
   
    To add **ALL** unstaged files onto the stage, type `git add .`.
   
    To remove specific file(s) from the stage, type `git checkout FILENAME.md`. As with `git add`, you can always add extra file names to remove multiple files from the stage at once. Removing files from the stage **WON'T** delete our files in our working directory.
   
    Once we have added our files onto the stage, you can verify them by running `git status` again. The files highlighted in green should reflect the files that we have added onto the stage with `git add`.
  
2. **Commiting files on our stage.**  

    Once we have our files added onto the stage, we can now commit those files. Commiting simply means taking a snapshot of our files with all of our changes. We can then push these commits onto GitHub.
   
    To commit our files, we can use `git commit -m "MESSAGE"`, where the `-m` flag stands for "message", which allows us to enter a string to be used as a commit message. 
    
    Commit messages are useful for keeping track all of the changes we have done over time. In additon, commit messages should be short and concise, and also in **PRESENT** tense, not *past* tense even though it seems very tempting.
    
    🎉 Tada, you have succesfully created your first commit!
    
3. **Pushing our commit to our remote repository.**

    

---
## Rolling Back Changes
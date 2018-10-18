# GitHub Tutorial

_by Alex_

---
## Git vs. GitHub

Git allows for version control of your files. It allows you to save snapshots (commits) of your files throughout different file changes. Git does not depend on GitHub. It is local repository.  
  
GitHub, on the other hand, is a remote repository. It *requires* Git (unless you want to upload files manually). GitHub allows you to create remote repositories, where you can use Git to push your commits to the remote repository. Because it is a remote repository, it allows for collaboration with multiple people.

---
## Initial Setup

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
## Repository Setup

If you do not have a GitHub account, create one [**here**](https://github.com/join?source=header-home)

After that, you can click [**here**](https://github.com/alexy4744?tab=repositories) to view all your repositories *(or click on your avatar and click "Your Repositories" in the dropdown)*.

You should see a green button called **New** on the upper right side of your screen.
<!-- put new button screenshot here -->

Now enter your repository name, it should match the name of your local repository. Then click on "Create Repository".

Now, you have both your local and remote repositories set up.

However, we need to establish a connection between our local and remote repository so that we can push commits via the command line.

In order to establish a SSH connection with between our local and remote, we first need to get a SSH key from our IDE. Each IDE varies, but in order to get one from Cloud9, what we can go [here](https://c9.io/account/ssh) and copy the first public SSH key for public repositories, or the second one for private repositories.

---
## Workflow & Commands



---
## Rolling Back Changes
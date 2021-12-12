# Exploring Git and GitHub
## DAY 1

### Recording of the session
[Exploring Git and GitHub - Day 1](https://drive.google.com/open?id=13AP9Q1zztNGPmlkE-cXg3DZ-kBOz_8PN&authuser=dataanalyticsclub.dduc%40gmail.com&usp=drive_fs)

### __How to install git?__
Visit the git scm [website](https://git-scm.com/downloads) and download the correct version depending on your OS.
- [Windows](https://git-scm.com/download/win)
- [Linux / Unix](https://git-scm.com/download/linux)
- [macOS](https://git-scm.com/download/mac)

Verify that the installation is successful by running this command in your terminal / command prompt / powershell:
```bash
git --version
```
If the installation was successful, then the currently installed version will be displayed, else an error will be displayed. If you face any issues during installation, kindly raise an issue.

### Configure git to use with Github and similar platforms
If you don't have a GitHub account yet, you can create it [here](https://www.github.com). Run the following commands to set up your git configuration to use your name and e-mail when you make changes and commits to the repository.
```bash
git config --global user.name 'Your Name'
git config --global user.email 'your email'
```
Now when you make any commits all the git based platforms will attribute the changes to you and your email.

### Initialize a folder with git
Inside the folder where your source code and related files are located, run:
```bash
git init -b main
```
Once you have run the command, a new folder named `.git` will created inside your directory which will keep all the files related to source control.

### Tracking files
Once you have initialized your folder with git, you can start tracking your files and start making changes without worrying about your currently stable version.

When you first create a new file, it is marked as untracked. Once you have written something you need to stage the file and send it to the 'staging area'. You can do this in one of the following ways.
- Stage all files at once:
```bash
git add .
```
- Stage only selected files:
```bash
git add filename filename ... filename
```

After adding the files to the staging area, it's now time to commit these changes. Commit is time when git takes a snapshot our code and keeps it in it's database. It is always a good practice to not make commits that have very large modifications and to accompany each commit with a message.

Everything that is in the staging area will be commited. There are two ways to create a commit depending on the message you want to accompany with it.
- If the commit has some very minor patches or fixes, you can commit in this format
```bash
git commit -m 'Your message here'
```
- If you want to include a multi line commit with heading and description, then simply write
```bash
git commit
```
This will open a text editor where you can write your commit message in this format.


    Heading

    Start your description from here
    - Point 1
    - Point 2
    - Point 3

### Adding our repository to Github
Once we have made some commits to our repository on our local machine, we can upload it to any web hosted git repository platforms and track our code in the cloud and collaborate with other people. Here's how to add your local repo to GitHub.
- Create a new repository in GitHub.
- Do not initialize it with README or .gitignore.
- Once the repository is created in github, run these commands based on your repository and settings.
```bash
git remote add origin  <REMOTE_URL> 
# Sets the new remote
git remote -v
# Verifies the new remote URL
git push origin main
# Pushes the changes in your local repository up to the remote repository you specified as the origin
```
## DAY 2

Once you have setup your repository in GitHub, you can always retrieve the latest working copy of your code and start working on it, in case of any system failure. 

### __Cloning your repository__
In case you lose the source code from your personal computer, you can always clone it from GitHub. To do this:
1. Go to your repository page.
2. Click the Code button.
3. Copy the URL being displayed.
4. Go to terminal/cmd/powershell in your PC, and type the following command:
```bash
git clone 'paste the URL here'
```
5. Press enter and the GitHub repository will be cloned as is in the folder, where you have run this command.

### __Syncing changes in your local copy with GitHub repo__
Once you have two copies of your source code or repo, you will want to keep those synced with each other so that both are updated to the latest version and have all the changes being made.

You will have to do this in two parts:
1. __Fetching changes from the cloud repo__  
To do this, you will have to pull the changes made into the repo and merge them with your local copy.

```bash
git fetch --all
# this will fetch the changes from all branches in all remotes (if there are more than one remote source)
```

```bash
git fetch origin --all
# this will fetch the contents from all the branches present in the remote labelled as origin, which usually is the default name of the primary remote
```

```bash
git pull
# this will fetch the contents from the origin and merge them into current branch
```

```bash
git pull <remote_name> <branch_name>
# this will fetch all the changes from the branch in the given remote and merge it into the current local branch
```

2. __Pushing your changes to the cloud repo__  
Let's say you made some changes in your local repo and now you want to syncronize the changes with the cloud repo so that it remains updated. First you will pull any changes from the cloud repo, using the above commands, and then after resolving merge conflicts, if any, you will push your code using the `git pull` command.

```bash
git push <remote_name> <branch>
# this will push the contents of your current local branch to the remote branch you specified.
```

```bash
git push <remote_name> --all
# this push all the branches from the local repo to the cloud repo
```
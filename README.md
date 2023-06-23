# Git

### What is Git?
Git is a popular version control system. It was created by Linus Torvalds in 2005, and has been maintained by Junio Hamano since then.

It is used for:
- Tracking code changes
- Tracking who made changes
- Coding collaboration

### Basic working of Git
- Initialize Git on a folder, making it a **Repository**
- Git now creates a hidden folder to keep track of changes in that folder
- When a file is changed, added or deleted, it is considered **modified**
- You select the modified files you want to **Stage**
- The **Staged** files are **Committed**, which prompts Git to store a **permanent** snapshot of the files
- Git allows you to see the full history of every commit.
- You can revert back to any previous commit.
- Git does not store a separate copy of every file in every commit, but keeps track of changes made in each commit!

### Getting Started
You can download Git for free from the following website: [https://www.git-scm.com/](https://git-scm.com/)

#### Check Installation
Open git bash (for windows) or built in terminal(for Mac and Linux) and run the following command to make sure you have installed git properly

```bash
git --version
```

If everything was installed properly you should get the following output

```bash
git version 2.38.0.windows.1
```

#### Configure Git
Now you should configure git with your username and email which is important to let git know who you are so it can track the changes you made

```bash
git config --global user.name "username" 
git config --global user.email "user@name.com"
```

Use the above email to register with GitHub which will be covered later on

#### Initialize Git
Navigate to the folder you want to use git with and run the the command below to initialize git

```bash
git init
```

Git now knows that it should watch the folder you initiated it on and creates a hidden folder to keep track of changes.

#### Adding Files to Git

To work with git we need some files to version control over. So let's create a simple webpage using basic HTML and CSS

```index.html```
```html
<html>  
	<head>  
		<title>Hello World!</title>  
	</head>  
	<body>  
		<h1>Hello world!</h1>  
		<p>This is the first file in my new Git Repo.</p>  
	</body>  
</html>
```

You can check the status of your repo by running

```bash
git status
```
This will give you a overall status of your repo like if there are any changes to commit, or if there is any changes that needed to be pulled etc.

Now add your `index.html` to your repo by running the following command

```bash
git add index.html
```
Or if you to add multiple files you can simply run

```bash
git add .
```

or

```bash
git add --all
```

This will add all the unadded files to the repo

This process is called staging the environment

#### Committing files to Git

Adding commits keep track of our progress and changes as we work. Git considers each  `commit`change point or "save point". It is a point in the project you can go back to if you find a bug, or want to make a change.

A commit always has a message (make it concise and meaningful)

Commit the staged files by running the following command

```bash
git commit -m "First Commit!"
```

Note that staging is not always necessary you can directly commit files without staging as well by directly running the `git commit` command

You can view the history of commits for a repo by using the following command

```bash
git log
```

#### Branching in Git

In Git, a `branch` is a new/separate version of the main repository.

Let's say you have a large project, and you need to update the design on it.

How would that work without and with Git:

Without Git:

- Make copies of all the relevant files to avoid impacting the live version
- Start working with the design and find that code depend on code in other files, that also need to be changed!
- Make copies of the dependant files as well. Making sure that every file dependency references the correct file name
- EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
- Save all your files, making a note of the names of the copies you were working on
- Work on the unrelated error and update the code to fix it
- Go back to the design, and finish the work there
- Copy the code or rename the files, so the updated design is on the live version
- (2 weeks later, you realize that the unrelated error was not fixed in the new design version because you copied the files before the fix)

With Git:

- With a new branch called new-design, edit the code directly without impacting the main branch
- EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
- Create a new branch from the main project called small-error-fix
- Fix the unrelated error and merge the small-error-fix branch with the main branch
- You go back to the new-design branch, and finish the work there
- Merge the new-design branch with main (getting alerted to the small error fix that you were missing)

Branches allow you to work on different parts of a project without impacting the main branch.

When the work is complete, a branch can be merged with the main project.

You can even switch between branches and work on different projects without them interfering with each other.

Branching in Git is very lightweight and fast!

#### Creating a new Branch in Git

Create a new branch by running the following command

```bash
git branch <branch-name>
```

You can see all the branches and which branch you are currently on using the following command

```bash
git branch
```

To move between branches use the following command

```bash
git checkout <branch-name>
```

Now any changes you made in this new branch will not impact the main branch until you merge it

It is like a copy of the project where you can write bad code without the fear of messing up the entire project

After creating the new branch you have to stage it and commit it do so using the following commands

```bash
git add --all
```

or

```bash
git add .
```

And commit using

```bash
git commit -m <message>
```

**Note: Every single branch you create if branched off from the main branch**

#### Merging branches in Git

Now that you are happy with the code you wrote on your new branch you want to merge it with the main branch. Merging is basically adding the changes you made to a branch to the main branch. You can do so by using the following command

```bash
git merge <branch-name>
```

#### Ctrl + Z

Suppose you are working on a commit but then you realise the damage you have done is beyond saving and nothing is working well then `git reset` and `git revert` are here to your rescue.
There are 2 scenarios here:

1. **Hard delete unpublished commits**
	Suppose you have made some changes but have not committed those changes yet and want to go back to the previous commit and discard all the changes you have made so far you can do so by running the following command
	
```bash
# This will destroy any local modifications.
# Don't do it if you have uncommitted work you want to keep.
git reset --hard 0d1d7fc32

# Alternatively, if there's work to keep:
git stash
git reset --hard 0d1d7fc32
git stash pop
# This saves the modifications, then reapplies that patch after resetting.
# You could get merge conflicts, if you've modified things which were
# changed since the commit you reset to.

```

2. **Undo published commits with new commits**
	On the other hand, if you've published the work, you probably don't want to reset the branch, since that's effectively rewriting history. In that case, you could indeed revert the commits. With Git, revert has a very specific meaning: create a commit with the reverse patch to cancel it out. This way you don't rewrite any history.
	
```bash
git revert --no-commit 0766c053..HEAD // here 0766c053 is the commit ID replace it with                                          the commit you wanna revert to
```


# GitHub

### What is GitHub?
GitHub is a web-based Git or version control repository on the Internet with a hosting service. It offers the distributed version control and source code management (SCM) functionality of Git as well as adding its own new features.

#### Creating a repo

Create a GitHub account using the username and email you used while setting up Git and log in to it and create a repository.

#### Push Local Repository to GitHub

Since we have already set up a local Git repo we can simply push it to our repo in GitHub but before that we have to add the remote repo to our local repo by running the following command:

```bash
git branch -M main
git remote add origin <remote-repo-URL>
```

You can get the URL from your repo on GitHub

Now to push the changes simply run the command below:

```bash
git push -u origin main
```

#### Pull updates from Repository on GitHub

Now let's say your peers with access to the repo has made some changes and pushed it to the repo on GitHub, you would want those changes. To get the changes simply run the following command:

```bash
git pull
```

This command will pull the changes only from the current branch you are working on

Suppose new branches were created to get those branches simple run:

```bash
git fetch --all
```

This will fetch all the branches

Now you are armed with the basics of Git and GitHub! [Refer this](https://education.github.com/git-cheat-sheet-education.pdf) for a cheat sheet for all Git commands.

All the best and code on 🤘🤘

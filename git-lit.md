# Git

## What is version control?
One way to think about it is in the context of some software tool you currently use. Every few months you get a new 'version' of the tool you are using. The code that was written to create the software tool is the same original files, but in this new version some of the files may have been changed to add a new feature or fix a bug (broken code). Git is one of the tools that developers use to be able to facilitate multiple versions of code.

### Some other analogies:

- track changes or history in a word/google doc
- for gamers a checkpoint 

## Why use version control/git?
- code at various stages or versions
- living document - history
- collaboration

### Why use git specifically?
The git documentation covers this topic very well [here](https://git-scm.com/about) if you want to more in depth to why git.

## Github vs git
### git
git is a command line tool (in your terminal), that allows us to do get all the benefits described above. You can do all you need locally (on your computer) without connect to the internet. See [Why git?]() section for more detail, but it's local capabilities are one of it's main advantages. 

### Github
Github is a web application built on top of git. It adds some additional functionality and some nice UIs (user interfaces) to make things easier to read. The main benefit is it easily helps us collaborate with other developers. We can put our code up on Github and others can collaborate on the project, use our code as an example, give us feedback on what we are writing, etc.

You may here people say "remote repository" this is what github is. A place not our our computer where we can store our code. 

There are other similar services Github is just one that is popular and we will be using during the workshop.

## Git basics - Commands and theory
We are going to learn five basic command that will get you started with git in your terminal. You will see references to these throughout the curriculum, but feel free to come back to these notes if you need a reminder.

#### Commits
Commits are how we are able to go forward or back.

#### Workflow Diagram
We will reference this diagram in the descriptions below.

![git workflow diagram](imgs/git-workflow.png)

#### git init
This turns the folder your code is in into a local git repository.

```
$: cd project-folder
$: git init
```
#### git status
This command prints out the current state of your local repository. It will show you the files git is tracking or not, what changes have been made, and what changes are staged for commit. This is a command developers run frequently and often between different stages.
 
```
$: git status
```
#### git add
When you are happy with a change (or changes) you need to move them to the staging area. The staging area files are in green when you run a ```git status```. All staged changes will be included in your next commit.

#### git commit -m 
Like mentioned earlier, a commit is the snapshot in time of the code. This command makes that snapshot. The command takes a message that describes the changes being committed.

```
$: git commit -m "useful message describing the change"
```
#### create a remote and link to remote repository
Instructions for how to do this can be found [here](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/).

#### git push
Now the changes are in the local repository it is time to put them on the remote repository and share the code you wrote (to share it with a friend!). This command will do that!

```
$: git push
```

## More Resources
- [git documentation](https://git-scm.com/doc)
- [Github Cheat Sheet](https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf)
- [Visual Git Cheat Sheet](http://ndpsoftware.com/git-cheatsheet.html)

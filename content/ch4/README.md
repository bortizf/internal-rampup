# Source Code Management – SCM
Also refered as Version Control Systems (VCS).
The purpose of version control is to allow software teams track changes to the code, while enhancing communication and collaboration between team members. Version control facilitates a continuous, simple way to develop software. It serves as a safety net to protect the source code from irreparable harm, giving the development team the freedom to experiment without fear of causing damage or creating code conflicts.

If developers code concurrently and create incompatible changes, version control identifies the problem areas so that team members can quickly revert changes to a previous version, compare changes, or identify who committed the problem code through the revision history. With version control systems, a software team can solve an issue before progressing further into a project. Through code reviews, software teams can analyze earlier versions to understand how a solution evolved.
## Why use version control?
When you work in a project, you manage information across a lot of different files. Imagine you write scripts that might evolve over time. For example, you might add new features to your script or take into account additional conditions or modify the scope of systems where the script will be executed. You also manage configuration related to your infrastructure like the default settings on an application or the IP addresses assigned to the computers in your fleet. This information changes over time as the security requirements increase. The fleet grows or new versions of software gets deployed. When trying to manage change , it's super important to have detailed historical information for your configuration files and code. This let the team see what was modified and when, which can be critical to troubleshooting. It also provides a documentation trail that will let future IT specialists know why the infrastructure is the way it is, and it provides a mechanism for undoing a change completely. This way, we don't have to undo changes from memory and there's less chance of human error. We'll see this in action when we talk about rollbacks. 

Imagine this, you have to make a new function in a script. In this new feature, you remove a lot of code and add new code. Some time later you realize that the script starts to fail in cases where it worked before. So you try to remember what you did and ask if anyone changed anything else. To avoid these headaches, you can use a version control system to easily revert your code to the previous version or track changes. Since you know the last version that worked, you can check what is missing or even it would be safe to go back to that until you had time to fix the code, run some tests, and make sure everything works fine for all cases.
For this reason everything should be versionable! Even things like infrastructure and configuration.

### Benefits of using a VCS
### A complete long-term change history of every file.
This means every change made by many individuals over the years. Changes include the creation and deletion of files as well as edits to their contents. Different VCS tools differ on how well they handle renaming and moving of files. This history should also include the author, date and written notes on the purpose of each change. Having the complete history enables going back to previous versions to help in root cause analysis for bugs and it is crucial when needing to fix problems in older versions of software. If the software is being actively worked on, almost everything can be considered an "older version" of the software.

### Branching and merging.
Having team members work concurrently is a no-brainer, but even individuals working on their own can benefit from the ability to work on independent streams of changes. Creating a "branch" in VCS tools keeps multiple streams of work independent from each other while also providing the facility to merge that work back together, enabling developers to verify that the changes on each branch do not conflict. Many software teams adopt a practice of branching for each feature or perhaps branching for each release, or both. There are many different workflows that teams can choose from when they decide how to make use of branching and merging facilities in VCS.

### Traceability. 
Being able to trace each change made to the software and connect it to project management and bug tracking software such as Jira, and being able to annotate each change with a message describing the purpose and intent of the change can help not only with root cause analysis and other forensics. Having the annotated history of the code at your fingertips when you are reading the code, trying to understand what it is doing and why it is so designed can enable developers to make correct and harmonious changes that are in accord with the intended long-term design of the system. This can be especially important for working effectively with legacy code and is crucial in enabling developers to estimate future work with any accuracy.

While it is possible to develop software without using any version control, doing so subjects the project to a huge risk that no professional team would be advised to accept. So the question is not whether to use version control but which version control system to use.
## Type of VCS
Depending on a team's specific needs, a version control system can be local, centralized, or distributed. A local version control system stores files within a local system. Centralized version control stores changes in a single repository, this central repository can be located on a server or on a developer's local machine and are typically used in software development projects where a team of developers needs to share code and track changes. A distributed is a type of version control system that allows users to access a repository from multiple locations, this are often used by developers who need to work on projects from multiple computers or who need to collaborate with other developers remotely.
There are different systems for version control. Most populars are 
### Git
Git is the most popular option and has become synonymous with "source code management." Git is an open source distributed system that is used for software projects of any size, making it a popular option for startups, enterprise, and everything in between.
### Subversion
SVN is a widely adopted centralized version control system. This system keeps all of a project's files on a single codeline making it impossible to branch, so it's easy to scale for large projects. It's simple to learn and features folder security measures, so access to subfolders can be restricted.
### Mercurial
Mercurial is a distributed version control system that offers simple branching and merging capabilities. The system enables rapid scaling and collaborative development, with an intuitive interface. The flexible command line interface enables users to begin using the system immediately.

You are free to choose whatever you want, but we recommend git so we are going to focus this section to it. 

## First Steps With Git
So, what is Git in a nutshell? This is an important section to absorb, because if you understand what Git is and the fundamentals of how it works, then using Git effectively will probably be much easier for you. As you learn Git, try to clear your mind of the things you may know about other VCSs, such as CVS, Subversion or Perforce — doing so will help you avoid subtle confusion when using the tool. Even though Git’s user interface is fairly similar to these other VCSs, Git stores and thinks about information in a very different way, and understanding these differences will help you avoid becoming confused while using it.

The major difference between Git and any other VCS (Subversion and friends included) is the way Git thinks about its data. Git thinks of its data more like a series of snapshots of a miniature filesystem. With Git, every time you commit, or save the state of your project, Git basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. To be efficient, if files have not changed, Git doesn’t store the file again, just a link to the previous identical file it has already stored. Git thinks about its data more like a stream of snapshots.

### File States and Sections
The main thing to remember about Git if you want the rest of your learning process to go smoothly. Git has three main states that your files can reside in: modified, staged, and committed:

* Modified means that you have changed the file but have not committed it to your database yet.

* Staged means that you have marked a modified file in its current version to go into your next commit snapshot.

* Committed means that the data is safely stored in your local database.

This leads us to the three main sections of a Git project: the working tree, the staging area, and the Git directory.

* The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

* The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit. Its technical name in Git parlance is the “index”, but the phrase “staging area” works just as well.

* The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

### Git Worflow
The basic Git workflow goes something like this:

* You modify files in your working tree.

* You selectively stage just those changes you want to be part of your next commit, which adds only those changes to the staging area.

* You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.
## Installation and Setup
Follow next link to install git according your OS
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

Now that you have Git on your system, you’ll want to do a few things to customize your Git environment. You should have to do these things only once on any given computer; they’ll stick around between upgrades. You can also change them at any time by running through the commands again.
The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating:
```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
Again, you need to do this only once if you pass the --global option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the --global option when you’re in that project.
## Git Repository and Basic Flow
Repositories in GIT contain a collection of files of various different versions of a Project. These files are imported from the repository into the local server of the user for further updations and modifications in the content of the file.
You typically obtain a Git repository in one of two ways:

You can take a local directory that is currently not under version control, and turn it into a Git repository
```bash
$ cd /home/user/my_project
$ git init
```

You can clone an existing Git repository from elsewhere.
```bash
$ git clone <repository url> <path>
```

In either case, you end up with a Git repository on your local machine, ready for work.

Typically, you’ll want to start making changes and committing snapshots of those changes into your repository each time the project reaches a state you want to record.

Remember that each file in your working directory can be in one of two states: tracked or untracked. Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified, or staged. In short, tracked files are files that Git knows about.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

<p align="center">
<img style="width:400px; height:200px" src=imgs/file-states.png >
</p>

In order to begin tracking a new file, you use the command git add. To begin tracking the README file, you can run this:
```bash
$ git add README.md 
```
Then if you run the command git status you will see that your README file is now tracked and staged to be committed:
```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)

    new file:   README
```

You can tell that it’s staged because it’s under the “Changes to be committed” heading. If you commit at this point, the version of the file at the time you ran git add is what will be in the subsequent historical snapshot. 

Now that your staging area is set up the way you want it, you can commit your changes. Remember that anything that is still unstaged — any files you have created or modified that you haven’t run git add on since you edited them — won’t go into this commit. They will stay as modified files on your disk. In this case, let’s say that the last time you ran git status, you saw that everything was staged, so you’re ready to commit your changes. 
```bash
$ git commit -m "Story 182: fix benchmarks for speed"
[master 463dc4f] Story 182: fix benchmarks for speed
 2 files changed, 2 insertions(+)
 create mode 100644 README
 ```
Now you’ve created your first commit! You can see that the commit has given you some output about itself: which branch you committed to (master), what SHA-1 checksum the commit has (463dc4f), how many files were changed, and statistics about lines added and removed in the commit.

## Branching
A branch is similar in concept to other versioning systems, but in git it’s simply a pointer to a particular commit. As you make additional commits within a branch, the branch pointer moves to point to your latest one. To revert to a previous version of your code, the branch pointer is simply moved to point to another commit within that branch.
Understanding how these components work together is the key to understanding git.

Branching means you diverge from the main line of development and continue to do work without messing with that main line. In many VCS tools, this is a somewhat expensive process, often requiring you to create a new copy of your source code directory, which can take a long time for large projects.

Some people refer to Git’s branching model as its “killer feature,” and it certainly sets Git apart in the VCS community. Why is it so special? The way Git branches is incredibly lightweight, making branching operations nearly instantaneous, and switching back and forth between branches generally just as fast. Unlike many other VCSs, Git encourages workflows that branch and merge often, even multiple times in a day. Understanding and mastering this feature gives you a powerful and unique tool and can entirely change the way that you develop.

The default branch name in Git is master. As you start making commits, you’re given a master branch that points to the last commit you made. Every time you commit, the master branch pointer moves forward automatically.

What happens when you create a new branch? Well, doing so creates a new pointer for you to move around. Let’s say you want to create a new branch called testing. You do this with the git branch command:
```bash
$ git branch testing
 ```
This creates a new pointer to the same commit you’re currently on.
<p align="center">
<img style="width:400px; height:200px" src=imgs/branch-testing.png >
</p>
How does Git know what branch you’re currently on? It keeps a special pointer called HEAD. Note that this is a lot different than the concept of HEAD in other VCSs you may be used to, such as Subversion or CVS. In Git, this is a pointer to the local branch you’re currently on. In this case, you’re still on master. The git branch command only created a new branch — it didn’t switch to that branch.

To switch to an existing branch, you run the git checkout command. Let’s switch to the new testing branch:

```bash
$ git checkout testing
 ```
This moves HEAD to point to the testing branch.

For more information we highly recommend you to take a look to this documentation, essentially volume 2 and 3
* https://git-scm.com/book/en/v2

## Useful Commands

### Starting

| Command | Description |
| ------- | ----------- |
| `git config --global user.name {username}`  | Set globally User Name | 
| `git config --global user.email {useremail}`  | Set globally User Email | 
| `git config --global --list` | Get global config |
| `git init` | Initialize a local Git repository |
| `git clone {url}` | Create a local copy of a remote repository |

### Basic Usage

| Command | Description |
| ------- | ----------- |
| `git status` | Check status of files |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |
| `git reset file-name.txt]` | This command unstages the file, but it preserves the file contents. |
### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging | 

For more information about commands you can follow this sources
* https://docs.github.com/en/get-started/using-git/about-git
* https://dzone.com/articles/top-20-git-commands-with-examples


## Branching Strategies 
A branching strategy is something a software development team uses when interacting with a version control system for writing and managing code. As the name suggests, the branching strategy focuses on how branches are used in the development process.

One major purpose of a version control system is to enable a collaborative development environment without overlapping or affecting the codebase. There, each team member modifying the same source code will inevitably be making conflicting code changes. However, we can avoid such conflicts with a version control system by using branches when writing and merging code to a master branch to create the end product.

A properly implemented branching strategy will be the key to creating an efficient DevOps process. DevOps is focused on creating a fast, streamlined, and efficient workflow without compromising the quality of the end product.

A branching strategy helps define how the delivery team functions and how each feature, improvement, or bug fix is handled. It also reduces the complexity of the delivery pipeline by allowing developers to focus on developments and deployments only on the relevant branches—without affecting the entire product.
## Selecting a Branch Strategy 
The selection process for a branching strategy depends entirely on the users and the project requirements. Factors like the development method, scale, user preferences highly impact this selection. Additionally, other factors like CI/CD tools decide what branching strategies can be used in your DevOps pipeline.

Branching strategies that do not align or make it more difficult to implement Continuous Integration and Continuous Delivery in DevOps pipelines should not be used in a DevOps environment.

The most common branching strategies are

### Git Flow
Git Flow is the most widely known branching strategy that takes a multi-branch approach to manage the source code. This approach consists of two main branches that live throughout the development lifecycle.

### GitHub Flow
As the name suggests, this strategy was introduced by GitHub, aiming to provide a simple and lightweight approach to manage the development. It adheres to the following guidelines when managing the source control with a single primary branch.

### Trunk Based Deployment
The Trunk Based Development strategy involves developers integrating their changes directly into a shared trunk (master) at least once a day. This shared trunk is always in a releasable state. Developers can pull from this trunk, create a local repository, and then push the code to the shared trunk.

This regular integration enables developers to view each other’s changes quickly and immediately react if there are any conflicts.

### GitLab Flow
The GitLab strategy combines feature-driven development and feature branches with issue tracking. This strategy is similar to GitHub flow yet includes environmental branches such as development, pre-production, and production.

In GitLab Flow, development happens in one of these environmental branches, and verified and tested code is merged to other branches until they reach the production branch

For more information about this we highly recommend to take a look to this sources

* https://www.bmc.com/blogs/devops-branching-strategies
* https://www.flagship.io/git-branching-strategies/
  
## GitOps
GitOps is a set of practices that are aimed at managing the underlying infrastructure of an application. It utilizes Git as the source code management tool for managing the infrastructure code. In other words, GitOps is an evaluation of infrastructure as code and DevOps practices which uses Git as the single source of truth for provisioning infrastructure declaratively.
GitOps allows developers or the Ops team to declare their infrastructure as code and version control them via Git. Whenever a new change is required, a pull request with the new change is created, executing the CI/CD pipeline to provision or modify the infrastructure.

For more information about GitOps we recommend this source
https://www.bmc.com/blogs/gitops-cloud-native-app-delivery/
## Challenges
* For gaming practice we suggest you to do at least one of the following websites. If you want you can do all of these:
  * https://learngitbranching.js.org/
  * https://ohmygit.org/
  * https://gitexercises.fracz.com/
  * https://www.w3schools.com/GIT/exercise.asp?filename=exercise_getstarted1

* Create repositories for your scripts and next challenges
* Select a branching model and apply it to your repositories. Make a diagram explaining the branching model. 
* You need to apply that strategy to every repository you’ll use for this RampUp. For example, if you decide to upload your scripts (refer to Scripting) of your infrastructure code (refer to IaC) in different repos, apply that strategy in every single one of those repos. Even if those repos are not created yet, when you do so, apply a branching strategy to them (it could be different though)
  
## References
* https://about.gitlab.com/topics/version-control/
* https://www.atlassian.com/git/tutorials/what-is-version-control
* https://www.geeksforgeeks.org/version-control-systems/
* https://danielmiessler.com/study/git/
* https://www.geeksforgeeks.org/what-is-a-git-repository/
* https://git-scm.com/book/en/v2/
* https://www.bmc.com/blogs/devops-branching-strategies/#:~:text=What%20is%20a%20branching%20strategy,used%20in%20the%20development%20process.





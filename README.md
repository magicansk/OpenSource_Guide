# OpenSource Guide  

## Contribution Guidelines

- [Prerequisites](#prerequisites)
- [Forking The Project](#forking-the-project)
- [Create A Branch](#create-a-branch)
- [Creating A Pull Request](#creating-a-pull-request)
- [After PR](#after-pr)
- [Next Steps](#next-steps)
- [Resources](#resources)  
- [Quick Review](#quick-review)

### Prerequisites  
- Markdown 

### Forking the Project  
#### Setting Up Your System

1. Install [Git](https://git-scm.com/) or your favorite Git client.
2. (Optional) [Setup an SSH Key](https://help.github.com/articles/generating-an-ssh-key/) for GitHub.
3. Create a parent projects directory on your system. For this guide, it will be assumed that it is `/mean/`

#### Forking Respository

1. Go to the top level repository: <https://github.com/magiansk/InfoSec_Practice>
2. Click the "Fork" Button in the upper right hand corner of the interface ([More Details Here](https://help.github.com/articles/fork-a-repo/))
3. After the repository has been forked, you will be taken to your copy of the repo at `yourUsername/InfoSec_Practice`  

#### Cloning Your Fork

1. Open a Terminal / Command Line / Bash Shell in your projects directory (_i.e.: `/yourprojectdirectory/`_)
2. Clone your fork of InfoSec_Practice

```bash
$ git clone https://github.com/yourUsername/InfoSec_Practice
```  

* Make sure to replace `yourUsername` with your GitHub Username  
  This will download the entire Fork repo(_i.e. InfoSec Practice_) to your projects directory. 


#### Setup Your Upstream

1. Change directory to the new InfoSec_Practice directory  
```bash 
cd InfoSec_Practice
```  
2. Add a remote to the official repo:

```bash
$ git remote add upstream https://github.com/magicansk/InfoSec_Practice.git 
```  

Congratulations, you now have a local copy of the remote official repo!

#### Maintaining Your Fork

Now that you have a copy of your fork, there is work you will need to do to keep it current.

* Rebasing from Upstream

  Do this prior to every time you create a branch for a PR:

  1. Make sure you are on the `NewBranch` branch   
   ```bash
   $ git status
   On branch NewBranch
   Your branch is up-to-date with 'origin/NewBranch'.
   ```

   If your aren't on `NewBranch`, resolve outstanding files / commits and checko   ut the `NewBranch` branch
   ```bash
   $ git checkout NewBranch
   ```  

   2. Do a pull with rebase against `upstream`  
   ```bash  
   $ git pull --rebase upstream NewBranch
   ```  
   This will pull down all of the changes to the official NewBranch branch, without making an additional commit in your local repo.

   3. (_Optional_) Force push your updated NewBranch branch to your GitHub fork

   ```bash 
   $ git push origin NewBranch --force
   ```
   This will overwrite the NewBranch branch of your fork.

### Create A Branch

Before you start working, you will need to create a separate branch specific to the issue / feature you're working on. You will push your work to this branch.

#### Naming Your Branch

Name the branch something like `fix/xxx` or `feature/xxx` where `xxx` is a short description of the changes or feature you are attempting to add. For example `fix/email-login` would be a branch where you fix something specific to email login.

#### Adding Your Branch

To create a branch on your local machine (and switch to this branch):

```bash 
$ git checkout -b [name_of_your_new_branch]
```

and to push to GitHub:

```bash
$ git push origin [name_of_your_new_branch]
```

##### If you need more help with branching, take a look at _[this](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)_.

### Creating A Pull Request

#### What is a Pull Request?

A pull request (PR) is a method of submitting proposed changes to the Repo (or any Repo, for that matter). You will make changes to copies of the
files which make up InfoSec_Practice in a personal fork, then apply to have them
accepted by magicansk proper.

#### Need Help?

 Issue Mods and staff are on hand to assist with Pull Request
related issues in our [Contributors chat room](https://gitter.im/InfoSec_Practice/Contributors).

#### Important: ALWAYS EDIT ON A BRANCH

Take away only one thing from this document: Never, **EVER**
make edits to the `NewBranch` branch. ALWAYS make a new branch BEFORE you edit
files. This is critical, because if your PR is not accepted, your copy of
NewBranch will be forever sullied and the only way to fix it is to delete your
fork and re-fork.

#### Methods

There are two methods of creating a pull request for Repository: 

-   Editing files on a local clone (recommended)
-   Editing files via the GitHub Interface

*  Method 1: Editing via your Local Fork _(Recommended)_

This is the recommended method. Read about [How to Setup and Maintain a Local
Instance of Repository](#maintaining-your-fork).

1.  Perform the maintenance step of rebasing `NewBranch`.
2.  Ensure you are on the `NewBranch` branch using `git status`:

```bash
$ git status
On branch NewBranch
Your branch is up-to-date with 'origin/NewBranch'.

nothing to commit, working directory clean
```

1.  If you are not on NewBranch or your working directory is not clean, resolve
    any outstanding files/commits and checkout NewBranch `git checkout NewBranch`

2.  Create a branch off of `NewBranch` with git: `git checkout -B
    branch/name-here` **Note:** Branch naming is important. Use a name like
    `fix/short-fix-description` or `feature/short-feature-description`. Review
     the [Contribution Guidelines](#contribution-guidelines) for more detail.

3.  Edit your file(s) locally with the editor of your choice

4.  Check your `git status` to see unstaged files.

5.  Add your edited files: `git add path/to/filename.ext` You can also do: `git
    add .` to add all unstaged files. Take care, though, because you can
    accidentally add files you don't want added. Review your `git status` first.

6.  Commit your edits (follow any one of the below methods):

    a. Using the inbuilt script (_recommended_):
       - We have a [tool](https://commitizen.github.io/cz-cli/) that helps you to make standard commit messages. Simply execute `npm run commit` after you have added the necessary files as mentioned in the step earlier.

    b. Using Commitizen CLI:
       - If you are already using [commitizen](http://commitizen.github.io/cz-cli/), simply doing a `git cz` works as expected too!

7.  Squash your commits, if there are more than one.

8.  If you would want to add/remove changes to previous commit simply add the files as in Step 5 earlier,
    and use `git commit --amend` or `git commit --amend --no-edit` (for keeping the same commit message).

9.  Push your commits to your GitHub Fork: `git push -u origin branch/name-here`

10.  Go to [Common Steps](#common-steps)

*  Method 2: Editing via the GitHub Interface

Note: Editing via the GitHub Interface is not recommended, since it is not
possible to update your fork via GitHub's interface without deleting and
recreating your fork.

Read the [Wiki
article](http://forum.freecodecamp.org/t/how-to-make-a-pull-request-on-free-code-camp/19114)
for further information

### After PR 

1.  Once the edits have been committed, you will be prompted to create a pull
    request on your fork's GitHub Page.

2.  By default, all pull requests should be against the main repo, `NewBranch`
    branch.

3.  Submit a [pull
    request](http://forum.freecodecamp.org/t/how-to-contribute-via-a-pull-request/19368)
    from your branch to Magicansk's `NewBranch` branch.

4.  The title (also called the subject) of your PR should be descriptive of your
    changes and succinctly indicates what is being fixed.

    -   **Do not add the issue number in the PR title or commit message.**

    -   Examples: `Add Test Cases to Bonfire Drop It` `Correct typo in Waypoint
        Size Your Images`

5.  In the body of your PR include a more detailed summary of the changes you
    made and why.

    -   If the PR is meant to fix an existing bug/issue then, at the end of
        your PR's description, append the keyword `closes` and #xxxx (where xxxx
        is the issue number). Example: `closes #1337`. This tells GitHub to
        close the existing issue, if the PR is merged.

6.  Indicate if you have tested on a local copy of the site or not.


### Next Steps

#### If your PR is accepted

Once your PR is accepted, you may delete the branch you created to submit it.
This keeps your working fork clean.

You can do this with a press of a button on the GitHub PR interface. You can
delete the local copy of the branch with: `git branch -D branch/to-delete-name`

#### If your PR is rejected

Don't despair! You should receive solid feedback from the Issue Moderators as to
why it was rejected and what changes are needed.

Many Pull Requests, especially first Pull Requests, require correction or
updating. If you have used the GitHub interface to create your PR, you will need
to close your PR, create a new branch, and re-submit.

If you have a local copy of the repo, you can make the requested changes and
amend your commit with: `git commit --amend` This will update your existing
commit. When you push it to your fork you will need to do a force push to
overwrite your old commit: `git push --force`

Be sure to post in the PR conversation that you have made the requested changes.  

### Resources ###  
[Markdown1](https://www.markdowntutorial.com/)  
[Markdown2](https://guides.github.com/features/mastering-markdown/)  
[Fork the repo](https://help.github.com/articles/fork-a-repo/#platform-linux)    
[Pull Request](https://yangsu.github.io/pull-request-tutorial/)
[Github Beginner](http://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/)

### Quick Review ###  
[How to contribute practice?](https://github.com/magicansk/InfoSec_Practice/blob/master/CONTRIBUTORS_guide.md)

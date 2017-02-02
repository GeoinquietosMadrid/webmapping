# Git & GitHub

## 1. Git

**Git** is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

In order to learn how to use git have a look this resources:

* [Try Git](https://try.github.io/levels/1/challenges/1)
* [Aprende Git: ...y, de camino, GitHub](https://www.amazon.es/Aprende-Git-y-camino-GitHub-ebook/dp/B00K515GL2)
* [A Beginner's Tutorial to Git and GitHub](http://blog.udacity.com/2015/06/a-beginners-git-github-tutorial.html)

## 2. GitHub

**GitHub** is a web-based Git or version control repository and Internet hosting service. It offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. It provides access control and several collaboration features such as bug tracking, feature requests, task management, and wikis for every project.

### 2.1. GitHub beginners tutorial

To complete this tutorial, you need a [GitHub.com account](https://github.com/) and Internet access. You don’t need to know how to code, use the command line, or install Git (the version control software GitHub is built on).

#### STEP 1 - Create a Repository

A **repository** is usually used to organize a single project. Repositories can contain folders and files, images, videos, spreadsheets, and data sets – anything your project needs. We recommend including a README, or a file with information about your project. GitHub makes it easy to add one at the same time you create your new repository. 

In order to create a new repository follow these steps:

1. In the upper right corner, next to your avatar or identicon, click **+** and then select **New repository**.
2. Name your repository `web-map`.
3. Write a short description.
4. Select **Initialize this repository with a README**.
5. Click **Create repository**.

![repository](https://guides.github.com/activities/hello-world/create-new-repo.png)

#### STEP 2 - Create a branch

**Branching** is the way to work on different versions of a repository at one time.

By default your repository has one branch named `master` which is considered to be the definitive branch. We use branches to experiment and make edits before committing them to master.

When you create a branch off the `master` branch, you’re making a copy, or snapshot, of `master` as it was at that point in time. If someone else made changes to the `master` branch while you were working on your branch, you could pull in those updates.

This diagram shows:

* The `master` branch
* A new branch called `feature` (because we’re doing ‘feature work’ on this branch)
* The journey that feature takes before it’s merged into master

![branch](https://guides.github.com/activities/hello-world/branching.png)

In order to create a new branch follow these steps:

1. Go to your new repository `web-map`.
2. Click the drop down at the top of the file list that says **branch: master**.
3. Type a branch name, `readme-edits`, into the new branch text box.
4. Select the blue **Create branch** box or hit “Enter” on your keyboard.

![new-branch](https://guides.github.com/activities/hello-world/readme-edits.gif)

Now you have two branches, `master` and `readme-edits`. They look exactly the same, but not for long! Next we’ll add our changes to the new branch.

#### STEP 3 - Make and commit changes

Bravo! Now, you’re on the code view for your `readme-edits` branch, which is a copy of `master`. Let’s make some edits.

On GitHub, saved changes are called **commits**. Each commit has an associated **commit message**, which is a description explaining why a particular change was made. Commit messages capture the history of your changes, so other contributors can understand what you’ve done and why.

##### Make and commit changes

1. Click the `README.md` file.
2. Click the  pencil icon in the upper right corner of the file view to edit.
3. In the editor, write a bit about yourself.
4. Write a commit message that describes your changes.
5. Click **Commit changes** button.

![commits](https://guides.github.com/activities/hello-world/commit.png)

These changes will be made to just the README file on your `readme-edits` branch, so now this branch contains content that’s different from `master`.

#### STEP 4 - Open a Pull Request

Nice edits! Now that you have changes in a branch off of `master`, you can open a **pull request**.

Pull Requests are the heart of collaboration on GitHub. When you open a pull request, you’re proposing your changes and requesting that someone review and pull in your contribution and merge them into their branch. Pull requests show diffs, or differences, of the content from both branches. The changes, additions, and subtractions are shown in green and red.

As soon as you make a commit, you can open a pull request and start a discussion, even before the code is finished. You can even open pull requests in your own repository and merge them yourself. It’s a great way to learn the GitHub Flow before working on larger projects.

##### Open a Pull Request for changes to the README

1. Click the  **Pull Request** tab, then from the Pull Request page, click the green **New pull request** button.

![1-pr](https://guides.github.com/activities/hello-world/pr-tab.gif)

2. Select the branch you made, `readme-edits`, to compare with `master` (the original).
3. Look over your changes in the diffs on the Compare page, make sure they’re what you want to submit.

![2-pr](https://guides.github.com/activities/hello-world/diff.png)

4. When you’re satisfied that these are the changes you want to submit, click the big green **Create Pull Request** button.

![3-pr](https://guides.github.com/activities/hello-world/create-pr.png)

5. Give your pull request a title and write a brief description of your changes.

![4-pr](https://guides.github.com/activities/hello-world/pr-form.png)

When you’re done with your message, click **Create pull request**!

#### STEP 5 - Merge your Pull Request

In this final step, it’s time to bring your changes together – merging your readme-edits branch into the master branch.

1. Click the green **Merge pull request** button to merge the changes into master.
2. Click **Confirm merge**.
3. Go ahead and delete the branch, since its changes have been incorporated, with the **Delete branch** button in the purple box.

![merge](https://guides.github.com/activities/hello-world/merge-button.png)

## 3. References

* [Github Guides](https://guides.github.com/)
* [Git and GitHub learning resources](https://help.github.com/articles/git-and-github-learning-resources/)



# Multiplayer Git

This lab is intended to give you practice using git and GitHub _collaboratively_, with multiple people working on the same set of code. You will practice having multiple people push changes to a repository, as well as learn how to use [Github Issues](https://guides.github.com/features/issues/) to track and plan your work.

The lab should be completed **in your project teams**&mdash;use this opportunity to make sure everyone is able to work well together! Note that detailed instructions can be found in the embedded links to the documentation&mdash;make sure to follow and read those!

### Resources
- [Github Issues Module](https://guides.github.com/features/issues/)
- [Git Workflows (Atlassian)](https://www.atlassian.com/git/tutorials/comparing-workflows)

## Creating a new Repository
For this lab, **do not fork and clone this repository!** 

1. Instead, your team should create your _own_ [new public repository on GitHub](https://help.github.com/articles/create-a-repo/). You can name this repo something temporary like `team-lab-practice`, or this can even be the start of your group's project repo (named appropriately for your project). Note that only one team member should create this repository, as the whole team will be working from the same code.

    - You should initialize the repo "with a README" so that you'll have some starting code. 

2. Only one team member (call them Person #1) needs to create this repository, as the whole team will be working on the same code. But that person will then need to [add all team members as collaborators](https://help.github.com/articles/adding-collaborators-to-a-personal-repository/) to that repo.

3. Each person (including the original repo creator) will need to `clone` (_ but not fork_) that repo to their local machines. That way everyone will have a copy of the code!


## Creating Issues
GitHub provides a set of functionality (called **Issues**) to help keep track of work that should be done. As a group, read over the introduction to this module at [https://guides.github.com/features/issues/](https://guides.github.com/features/issues/).

1. In your GitHub repo, as a team, you should create two (2) issues:

    1. **Create a new file**
    2. **Complete the team practice lab**

    You don't need to assign these to anyone in particular (though in the future you should assign tasks to team members).


## Pushing and Pulling
Pick another team member&mdash;one who _didn't_ initially create the repo&mdash;to be "Person #2". 

1. This member should create a new file `index.html` (using VS Code or your favorite editor). Make this file contain a basic HTML template for a "to do list" that includes one item for now:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
       <meta charset="UTF-8">
       <title>To Do</title>
    </head>
    <body>
       <h1>To do list</h1>
       <ul>
          <li>Learn to collaborate with GitHub</li>
       </ul>
    </body>
    </html>
    ```
    
    (The thing to do can be whatever you want. _"Fight against incoming fascist governments"_ is a good one).

2. Person #2 should `add` and `commit` this new file. Be sure to include `"closes #1"` in your commit message to close the first issue you made (since you've now made a new file)!

3. Person #2 should then `push` the change to GitHub. After that, every other person should `pull` the change (from `origin master`), so that they have downloaded the latest version of the code.

    - This is the basic pattern: someone makes some changes, pushes them, and then others can pull down those changes onto their own computers.

    - You can also confirm that the first Issue you created has now been closed.
    
    - You can have Person #3 add a second item to the list and repeat the process for practice.

## Handling Conflicts
Of course, more likely you'll be working on the same code _at the same time_, so let's try that:

1. Make sure that everyone has pulled down the latest copy of the code. Use `git status` to confirm that each person's repository is up to date.

2. Have Person #3 change the **first** to-do item in some way. Make it a different thing, make it all caps, add more details, whatever.

    - `add` and `commit` this change **but do not push yet**.

    At the same time (need not be literally), have Person #4 change the **first** to-do item in some _other_ way. If you only have 3 people in your group, swing back around to Person #1.

    - `add` and `commit` this change **but do not push yet**.

3. Have Person #3 `push` their change, **then** Person #4. _What happened?_

    - Person #4 shouldn't be able to push, because there are changes on GitHub (Person #3's edit) that their uploads would conflict with. Since conflicts can't be resolved on GitHub, it won't even let you do that uploading.

4. Have Person #4 `pull` down the changes (Person #3's edit). This will cause a [merge conflict](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/). The whole team can help with _resolving_ this conflict.

    - In order to resolve this conflict and determine which item to keep, you'll need to **communicate with your team members**. Talk to them! Communication is key when collaboratively coding.

    - __Pro tip:__ use `git commit --no-edit` when resolving the merge conflict to use the "default' merge method.

5. Once the conflict is resolved, have Person #4 `push` the fixed version for everyone else to `pull`.

6. As a last step, have a team member make a last change to the webpage (maybe cross off any items you've done), and the commit that change with a `"closes #2"` message to close the last Issue. Make sure to `push` this change so Github and the rest of the team knows!

    
## Comparing Workflows
Doing teamwork with Github involves developing a "collaborative workflow": a development process by which everyone can do their work _at the same time_ but still keep the code working reasonable. There are [a couple of different common workflows](https://www.atlassian.com/git/tutorials/comparing-workflows) you might try. Use the rest of the lab time to look at these and decide **as a group** how you want to do your development work.

- [**Centralized Workflow**](https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow) is similar to what you've just done in lab: using a single repo (the one on GitHub) as a clearing-house for other changes. This is simple and easy to use, but it can lead to _a lot_ of merge conflicts if multiple people are working on the same code at the same time. Every time you need to pull changes, you'll have to check what changes they made to the section you're working on and watch out for stuff breaking. Automated testing can help catch these problems.

- [**Feature Branch Workflow**](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) is similar to what you've done with your homework assignments: each person can make a separate _branch_ to work on. This way you can pull down changes from the `master` branch (the one on GitHub), and only merge in your features when they are ready. That way the code on `master` is always working, and you'll never have to worry about pushing broken code!

- [**Gitflow Workflow**](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) is a professional workflow used by a number of different companies. It basically takes the "Feature Branch" model and defined a specific set of branches to work on, with each branch acting as a "gate-keeper" to the working code. You are welcome to try something like this in your group project, though it is not required.

The best rule of thumb for development is: **do not push broken code to `master`**. This will make sure that no one else "inherits" your bugs, leading to cascading and difficult to fix problems.


### Bonus: Slack Integration
If you wish to use Slack, you can [create a private channel](https://get.slack.help/hc/en-us/articles/201402297-Creating-a-channel) and then [integrate](https://get.slack.help/hc/en-us/articles/232289568-Use-GitHub-with-Slack) your GitHub repo into Slack. This way any changes that are pushed to the repo will post to your channel, so you can easily stay on top of your teammate's work! You will need to set this up for each repo you want to track.

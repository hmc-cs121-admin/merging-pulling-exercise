# Merging/Pulling Exercise

## Prerequisites 

(from https://github.com/StoneyJackson/github-workflow-activity/blob/rewrite/reference.md)

- You have a GitHub account and you know your username and password. If you
  don't have one, create one now.
- You have Git 2+ installed and configured.
- You know how to open a terminal and generally work from the command-line.
- You know enough of vi or vim to edit, move around in, save, and quit files.

## Learning Objectives
When you finish this exercise, you will be able to...
- Fork a repository you would like to contribute to
- Clone a forked repository to your local hard drive
- Create a new branch (via CLI and GitHub web interface)
- Make a pull request 
- Resolve merge conflicts

## Instructor:

- Creates a (public) repository
- Add an initial README.md
- Add an initial rainbow.md containing color names
- Share the github repo URL with the students
- Show pull requests and accept PRs 

## Students: 
Note: lines starting with [GitHub] should be done through GitHub's web interface.

### Get Ready (fork and clone)

- [GitHub] Fork the instructor's repo (`<ORIGINAL_REPOSITORY_URL>`) to your GitHub account

- [GitHub] Navigate to _your_ fork of the project. Use "Clone or download" to reveal _your_ fork's repository URL. This is the <FORKED_REPOSITORY_URL>.

- Clone the forked repository to your local hard drive:

  `git clone <FORKED_REPOSITORY_URL>  <LOCAL_REPOSITORY_DIRECTORY>`

### Make a change to your local file (rainbow.md)

- `cd` to the new directory you just cloned

  `cd <LOCAL_REPOSITORY_DIRECTORY>`

- Create a new branch and check out the branch to make a change. Call your branch: `<color-your_first_name-branch>`, for example:

  `git checkout -b red-firstname-branch`

  (Specifying `-b` causes a new branch to be created as if git-branch were called and then checked out.)

Let's edit `rainbow.md` to add you color and name to it using your favorite text editor.

- Add your name to the list: list your first name underneath your favorite color, for example, under the Red section,

  `red-firstname`

- Save and exit. You may now try `git status` to see the `rainbow.md` was modified but not added.

- Stage your changes to your local git repository (add):

  `git add rainbow.md`

- Save your changes to your local repo (commit):

  `git commit -m "added my color and name"`

  (The "added my color and name" part is a commit message. When you commit, you should always give a meaningful message showing what's done and changed.)

### Push your changes to a GitHub repo

- Now you can push the changes to your GitHub repo (the forked one)

  `git push`

  (Notice that you get a fatal error, for example:

  > fatal: The current branch green-jeho has no upstream branch.
  > To push the current branch and set the remote as upstream, use
  > 
  >    git push --set-upstream origin green-jeho

  The error is self-explanatory; your branch has no upstream branch. At this point, you basically have two options: 

  (1) set upstream (i.e., origin) for your current branch (i.e., `<<color-firstname-branch>>`): 

    `git push --set-upstream origin <<color-firstname-branch>>`

  (2) merge (fast-forward merge) your branch into master branch and push the new change to origin from the master branch:

  - Change branch to master (whose origin is already known)

    `git checkout master`

  - Merge `<<color-firstname-branch>>` into master branch
  
    `git merge <<color-firstname-branch>>` (After this point, your master branch and <<color-firstname-branch>> will be pointing to the same status; you can delete <<color-firstname-branch>> afterwards if you want as follows.)

  - Delete old branch (optional)
  
    `git branch -d <<color-firstname-branch>>` 

  - Finally, you are ready to push the chages recorded in master branch to your (forked) GitHub repo:
  
    `git push` (this will upload all the new/updated files to the gitHub repo pointed as origin)
  
### Create a Pull Request into the original instructor's repo

You're ready to create a PR (Pull Request)

- [GitHub] Pick a volunteer and let him/her make a pull request to the instructor's repo. 
  (Notice that GitHub checks the original (instructor's) repo and reports whether the changes conflict or not.) 

- In the main repo, the instructor merges the new change into master by approving the PR.

- Everyone should now sync their (forked) repo. See https://help.github.com/articles/syncing-a-fork/

- Note that people who selected the same color should now see a merge conflict.

- In case there's a conflict, you should resolve the conflict by opening the issue and change the file.

### Resolve the merge conflict
  
- Pick another volunteer with the same color and they can now commit their branch and submit a PR.

- Let the second person (with the same color) resolve the conflict.
  
- Repeat the above steps to integrate the new change.

- Other volunteers with different colors should now submit their changes, call pull requests, and experience merge conflicts.

## A Workflow considering GitHub web interface and local command line interface

| Remote (GitHub) Web Interface | Local Command Line Interface |
| --- | --- |
| Create a GitHub repo | --- |
| Fork a repo | (possible with hub) |
| (not possible) | Clone the remote (GitHub) repo to local repo |
| (possible) | Create/checkout new branches |
| (possible) | Create/edit files |
| --- | Stage (add) the files |
| --- | Commit the changes to local repo |
| (add/commit/push all at once) | Push the files to a remote (GitHub) repo |
| Pull request | (possible) |
| Resolve conflicts | (possible) |


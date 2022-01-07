# I'm learning git

*Alert: This is of no practical value to anyone other than myself.*

## Lesson 1: Cloning the `main` repository onto the Raspberry Pi 
*This assumes you've created your repository on github.*
You can confirm this by typing `git checkout main`. You will receive confirmation you are `Already on 'main'` and the `branch is up to date with 'origin/main'`
However, `git status` would be a better option if you just want to quickly know where you are.

`git clone` will clone the repository currently on the github server onto the RaspBerry pi.
For simplicity, we'll assume it's the master branch.

`git pull --all` will pull ALL the changes from github. If you have an elaborate branching system this might not be ideal. `git pull` will simply pull from whatever repository you have active.

## Lesson 2: Create a new document for the repository on the RasPi
*This assumes you know how to use vim to create a document and save it.*

1. You must `git add document_name` the document so github knows about it.
(If you try to commit without adding, you will get a message detailing the named `UNTRACKED FILES` along with a kindly-phrased suggestion to use `git add <files>` to include in what will be committed.)
2. Then you issue a `git commit`
3. Finally `git push origin main` the document up to github (main) branch on github on the (origin) github server.
(Assuming 2-factor is enabled, you will need your username, and the token you created in 'settings -> developer' on github. The token will take the place of your password.)

## Lesson 3: Branching
`git branch <branch name>` on the RasPi will create a branch but not switch you to it. In my case, I named it branch1.
`git checkout branch1` will switch you to that branch.
I created Document1 and I edited document1 while in branch1.
I added and committed both of them. Now I need to merge.

## Lesson 4: Merging
I've been in `branch1` but I need to get back to the `main` branch.
`git checkout main` will send me back into the main branch.
`git commit branch1 -m 'making a change from a branch'` will stage the file.
You need to get back to the main branch `git checkout main`
Finally `git merge branch1` will incorporate via "fast forward" all the changes you made while on branch1.
Finally finally, `git push origin main` to send the changes back up to github.

## Lesson 5: Deleting a branch
`git branch -d <branch name>` will delete the branch. 

## A quick aside: Logging (source: https://www.atlassian.com/git/tutorials/git-log)
`git log -1` can show you the last commit whereas `git log -4` will show the 4 most recent commits.

*There are more advanced options for logging.*

`git log --oneline` will itemize each commit on its own line as well as show the first line of the committed message. 

The chronological order of the `log` display descends from most recent commit at the top to the oldest commit at the bottom.

`git log --decorate` will give you quite a bit more information like tags and a longer commit message.

`git log --stat` also `git log --stat --oneline` will show the number of insertions/deletions on each commit. This is measured line by line with + and - signs indicating *relative number* of changes to the respective file.

`git log -p` will show the actual changes. This output can get out of hand.

`git shortlog` will show who contributed commits and how many they contributed.

`git log --graph` is useful when you want to visualize branching structure in a more complex repository.

## Test2
Created Test2 from github main branch

`git pull` on raspi and edited the Test2 file:

`git pull`  
`remote: Enumerating objects: 12, done.`  
`remote: Counting objects: 100% (11/11), done.`  
`remote: Compressing objects: 100% (7/7), done.`  
`remote: Total 8 (delta 4), reused 0 (delta 0), pack-reused 0`  
`Unpacking objects: 100% (8/8), 1.35 KiB | 345.00 KiB/s, done.`  
`From https://github.com/robrackn/learning-git`  
   `51517c4..c8aa0ba  main       -> origin/main`  
   `bda0347..c65d647  branch2    -> origin/branch2`  
`Updating 51517c4..c8aa0ba`  
`Fast-forward`  
 `Test2     | 1 +`  
 `document2 | 1 +`  
 `document3 | 1 +`  
 `3 files changed, 3 insertions(+)`  
 `create mode 100644 Test2`


attempted `git commit` without first adding the modified file:
`git commit`  
`On branch main`  
`Your branch is up to date with 'origin/main'.`  
`Changes not staged for commit:`  
  `(use "git add <file>..." to update what will be committed)`  
  `(use "git restore <file>..." to discard changes in working directory)`  
	`modified:   Test2`  
`no changes added to commit (use "git add" and/or "git commit -a")`


`git add Test2` on raspi:
-- file on github unchanged
-- file on raspi is modified


`git commit Test2` on raspi:
-- file on github remains unchanged
-- file on raspi remains modified
`git commit Test2<`  
`[main e1edc53] Editing file on RasPi. Completed git add and this is git commit`  
 `1 file changed, 1 insertion(+)`


`git push origin main` on raspi:   
-- file on github is updated and matches raspi   
-- file on raspi = file on github   
`pi@raspberrypi:~/Git/learning-git$ git push origin main`  
`Username for 'https://github.com': 'git username'`  
`Password for 'https://robrackn@github.com': 'used my key'`  
`Enumerating objects: 5, done.`  
`Counting objects: 100% (5/5), done.`  
`Delta compression using up to 4 threads.`  
`Compressing objects: 100% (3/3), done.`  
`Writing objects: 100% (3/3), 370 bytes | 123.00 KiB/s, done.`  
`Total 3 (delta 1), reused 0 (delta 0), pack-reused 0`  
`remote: Resolving deltas: 100% (1/1), completed with 1 local object.`  
`To https://github.com/robrackn/learning-git.git`  
   `c8aa0ba..e1edc53  main -> main`  

The file is sync'd on the raspi and on github in the main branch

## Test 3
I'm creating a new text file named *Patch2* on github site in the branch *robrackn-patch-2*
After editing the file, click `Propose new file`
Then you will either
1. `Create pull request` - open pull request that is ready for review.
2. `Create draft pull request` - this cannot be merged until it's marked ready for review

`git pull` on the RasPi to see a new branch exists:
`remote: Enumerating objects: 4, done.`  
`remote: Counting objects: 100% (4/4), done.`  
`remote: Compressing objects: 100% (2/2), done.`  
`remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0`  
`Unpacking objects: 100% (3/3), 730 bytes | 365.00 KiB/s, done.`  
`From https://github.com/robrackn/learning-git`  
 `* [new branch]      robrackn-patch-2 -> origin/robrackn-patch-2`  
`Already up to date.` 

Now, on github click `pull requests` where you will see the file(s) added.
Click "Create Patch2" where you will see the person who created the new file in the new branch wants to **merge 1 commit** into **main** from **robrackn-patch-2**
There are four tabs under the Pull Requests tab.
<table width="100%">
<tr>
<td width="25%">Conversation</td>
<td width="25%">Commits (1)</td>
<td width="25%">Checks</td>
<td width="25%">Files Changed (1)</td>
</tr>
</table>

Options here are to:
1. Create a merge commit (all commits from this branch will be added to the bas branch via a merge commit)
2. Squash and merge (The 1 commit from this branch will be added to the base branch)
3. Rebase and merge (The 1 commit from this branch will be rebased and added to the base branch)

Rebasing is one of two Git utilities that integrates changes across branches. The golden rule of rebasing is to *NEVER* do it on `public` branches. If anyone else is looking at the branch, find another way.

Its cohort is the `merge` command.
Merging is always a forward-moving change whereas `rebase` can rewrite history.
When you `branch` you necessarily end up with a forked history. When you `merge commit` you *non-destructively* tie together the histories of both branches. The down side is that new branch will have an extraneous merge commit every time an upstream change is required. It can muddy up the `main` branch history, making it hard for other developers to understand the history.

The `Rebase` option will append the entire new branch to the end of the `main` branch, incorporating all the commits into `main`. The project history is rewritten.

We will `Merge pull request` in this case.

On the RasPi, doing a `git pull` will show the following:
`remote: Enumerating objects: 21, done.`  
`remote: Counting objects: 100% (20/20), done.`  
`remote: Compressing objects: 100% (17/17), done.`  
`remote: Total 17 (delta 11), reused 0 (delta 0), pack-reused 0`  
`Unpacking objects: 100% (17/17), 4.55 KiB | 358.00 KiB/s, done.`  
`From https://github.com/robrackn/learning-git`  
   `d570f25..a3f9a3b  main       -> origin/main`  
`Updating d570f25..a3f9a3b`  
`Fast-forward`  
 `Patch2    |  1 +`  
 `README.md | 29 +++++++++++++++++++++++++++++`  
 `2 files changed, 30 insertions(+)`  
 `create mode 100644 Patch2`

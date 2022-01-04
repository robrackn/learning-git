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

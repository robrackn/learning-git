# I'm learning git

*Alert: This is of no practical value to anyone other than myself.*

## Lesson 1: Cloning the `main` repository onto the Raspberry Pi 
*This assumes you've created your repository on github.*
You can confirm this by typing `git checkout main`. You will receive confirmation you are `Already on 'main'` and the `branch is up to date with 'origin/main'`
However, `git status` would be a better option if you just want to quickly know where you are.

`git clone` will clone the repository currently on the github server onto the RaspBerry pi.
For simplicity, we'll assume it's the master branch.

## Lesson 2: Create a new document for the repository on the RasPi
*This assumes you know how to use vim to create a document and save it.*

1. You must `git add document_name` the document so github knows about it.
(If you try to commit without adding, you will get a message detailing the named `UNTRACKED FILES` along with a kindly-phrased suggestion to use `git add <files>` to include in what will be committed.)
2. Then you issue a `git commit`
3. Finally `git push origin main` the document up to github (main) branch on github on the (origin) github server.
(Assuming 2-factor is enabled, you will need your username, and the token you created in 'settings -> developer' on github. The token will take the place of your password.)

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

## So you want to roll back to a specific commit 

1. Look up the commit ID by either typing `git log` or going to your repo on github.com and click on the number of commits, to get to the commit history view. 

2. If there have not been merge commits been merge commits between now and the commit in the past you want to return to, then the following command ought to work:

`git revert COMMIT_HASH`

3. Then type: `git checkout <current branch>` (usually the current branch is master) to fix the detached HEAD. 

**Note**: If there _have_ been multiple merge commits between now and the commit in the past you want to return to, then you might need an alternative approach, using the `-m` flag with the `revert` command to revert individual commits going backwards in time. 

## Other resources on this topic:
* [Tutorial from Atlassian on Undoing Changes](https://www.atlassian.com/git/tutorials/undoing-changes)
* [Blog Post on same topic](https://code.likeagirl.io/how-to-undo-the-last-commit-393e7db2840b)
* [reset vs. revert vs. checkout](https://stackoverflow.com/questions/8358035/whats-the-difference-between-git-revert-checkout-and-reset)

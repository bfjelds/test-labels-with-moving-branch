# test-labels-with-moving-branch
If we create a branch and assign a label to a commit ... then radically change the branch with a force push ... does the label and its history survive???

Test
1.	Created a new [repo](https://github.com/bfjelds/test-labels-with-moving-branch) with main branch
2.	Created [commit 1](https://github.com/bfjelds/test-labels-with-moving-branch/commit/fb77a9c89c9e8a449682ec4dab17be8594da1225) and  [commit 2](https://github.com/bfjelds/test-labels-with-moving-branch/commit/a9b3c6297a96dc257380c376d825393dbb61f242)
3.	Created a tag for [commit2](https://github.com/bfjelds/test-labels-with-moving-branch/releases/tag/commit2)
4.	Created [commit 3](https://github.com/bfjelds/test-labels-with-moving-branch/commit/b170b6d20c9b5360e68c9ccdab0e2f1de58b4841) and created a new tag [commit3](https://github.com/bfjelds/test-labels-with-moving-branch/releases/tag/commit3)
5.	Checked out `commit2` and created local branch [`git checkout commit2` and `git checkout -b commit2`]
6.	Deleted main [`git branch -D main`]
7.	Created a new local main branch from ‘commit2’  branch [`git checkout -b main`]
8.	Created a [commit for the new main](https://github.com/bfjelds/test-labels-with-moving-branch/commit/b3e7e61ec9be54145b742950f906ec303c49a26a)
9.	Force pushed main [`git push -f origin main`]


# Results:

```
                                                  [original main] -- <commit b170, tag ‘commit3’>
                                                                 |
<init commit> -- <commit fb77> -- <commit a9b3, tag ‘commit2’> --|
                                                                 |
                                                       [new main] -- <commit b3e7, tag ‘new-main-commit3’>
```

The tags from the original main (`commit2` & `commit3`) survived the force push ... if you [view the tags from the code page](https://github.com/bfjelds/test-labels-with-moving-branch/tree/commit3), you can see the repo as it was for the tag and [view their history](https://github.com/bfjelds/test-labels-with-moving-branch/commits/commit3).

One bit of strangeness is that if you try to navigate to the [original main’s commit3 tag’s commit3](https://github.com/bfjelds/test-labels-with-moving-branch/commit/b170b6d20c9b5360e68c9ccdab0e2f1de58b4841), you get a warning that says `This commit does not belong to any branch on this repository, and may belong to a fork outside of the repository.`  But that seems correct (that commit is orphaned from a branching perspective) and harmless.



# First main, commit 1
main: commit 1!

# First main, commit 2
main: commit 2!!

# Second main, commit 3
main: 3rd commit???

## [[Git]] 

[remove the first commit ](https://stackoverflow.com/questions/10911317/how-to-remove-the-first-commit-in-git)
For me, the most secure way is to use the `update-ref` command:

```
git update-ref -d HEAD
```

It will delete the named reference `HEAD`, so it will **reset (softly, you will not lose your work) ALL your commits** of your current branch.

If what you want is to merge the first commit with the second one, you can use the `rebase` command:

```
git rebase -i --root
```

A last way could be to create an orphan branch, a branch with the same content but without any commit history, and commit your new content on it:

```
git checkout --orphan <new-branch-name>
```
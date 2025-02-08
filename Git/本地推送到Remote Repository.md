### [[Git]] [[push]]

```git
git push [remote repository URL]
```

有設定 remote URL的話，可以直接用 `git push` 就好
如果沒有設定目標網址，可以使用以下命令:
```git
git push --set-upstream origin master
```


### create a new repository on the command line

echo "# obsidian" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/tabbyBoots/obsidian.git
**git push -u origin main**

### push an existing repository from the command line

git remote add origin https://github.com/tabbyBoots/obsidian.git
git branch -M main
**git push -u origin main**
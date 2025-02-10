### [[Git]] [[pull]] [[更新分支]] 

```git
git pull origin training_ctr
```

### 推送本地分支進度到遠端儲存庫
#### `git push origin <branch_name>

### 下載遠端儲存庫所有分支更新並合併到本地分支
`git pull`
( `git pull` = `git fetch` + `git merge`)
### 將遠端的master分支合併到目前本地的master分支，要刪除分支則使用`-d [分支名稱]`參數
**[[-d 刪除跟 -D 刪除的差異]]**
#### `git pull origin master`
#### `git pull origin -d <分支名稱>`

### 將遠端的master分支合併到目前本地的master分支，冒號後是表示為本地分支
`git pull origin master:master`

### 下載所有遠端儲存庫最新程式碼
`git fetch --all`

### 下載遠端儲存庫master分支最新程式碼
`git fetch origin master`

[參考網站](https://blog.csdn.net/weiwenhou/article/details/106985423?source=post_page-----c5dc0639dd9--------------------------------)

[參考網站-branch](https://learngitbranching.js.org/?locale=zh_TW&source=post_page-----c5dc0639dd9--------------------------------)

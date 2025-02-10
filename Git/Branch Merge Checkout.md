### [[Git]] [[Branch Merge Checkout]]

# Branch
### 將某個Branch併入目前的分支，用以下指令
#### `git merge [branch的名稱]`

### Branch (分支)建立跟刪除
#### `git branch [分支名稱]  //建立分支，但是仍停留在原本的分支`
#### `git branch -d [分支名稱]  //刪除分支`

[-d 刪除跟 -D 刪除的差異](https://unix.stackexchange.com/questions/365944/what-are-the-differences-between-d-and-d-when-deleting-a-branch-in-git) 
### 顯示目前的Branch

#### `git branch //查本地分支`
#### `git branch -r //查遠端分支`
#### `git branch -a //查本地及遠端所有分支`

# Checkout
### 將`head`移動到該分支
#### `git check [分支名稱] //切換到這個分支`

#### `git checkout -b <分支名稱> //建立分支，並切換到這個分支`

# Merge
### 從目前分支跟指定分支合併(merge)
#### `git merge <分支名稱>`





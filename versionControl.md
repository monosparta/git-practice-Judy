# GIT版本控制

## GIT 起源
git最初的開發動力來自於BitKeeper和Monotone。git最初只是作為一個可以被其他前端（比如Cogito或Stgit）包裝的後端而開發的，但後來git核心已經成熟到可以獨立地用作版本控制。

由 Linus Torvalds 所發明，一開始的目的是為了管理 Linux Kernel 原始碼，他於2005/4 開始開發，2005/6 開始管理 Linux Kernel，2005/12 就釋出了 1.0 版。

## GIT 介紹
Git主要是拿來做軟體的版本控制與維護。在開發軟體時常常會有需多不同的版本，而這些都需要備份，在還沒有Git的以前大部分人都會使用複製的方式儲存多個不同版本的資料夾，而 Git是使用 DAG (Directed acyclic graph) 的儲存方式，利用有向無環圖來記錄 metadata 建構出 snapshots，相同內容只會有一份記錄。開分支也只是建立參考。

在 git 中 git會保留對於檔案的新增、修改或是刪除等操作的歷史紀錄，它也會記錄是誰在什麼時間對檔案做更動。

## Git 與 Github
* Git 是一個分散式版本控制軟體，可藉由它產生一個*儲存庫( git Repository)*。
* Github：支援 git 程式碼存取和*遠端托管儲存庫*的平台服務
* 關係像是本地端有一個 index.html，但可以放到 dropbox、Google Drive 進行雲端託管

## Git 常用指令
### 基本指令架構
![](https://i.imgur.com/bQLEGRA.png)


* 初始化數據庫： `git init`
* 查詢當前狀態：`git status`
    * 要將檔案加入到指定資料夾
* 將檔案加入到索引：`git add .`
:::info
檔案更新完status會變紅，要重新add 再commit
::: 

* 將索引檔案變成一個更新(commit)：`git commit -m "修改記錄"`
* 查看 commit 歷史紀錄： `git log` 
* 下載遠端數據庫： `git clone 數據庫網址`
* 更新遠端數據庫： `git push origin master`
* 從遠端儲存提取：`git pull`
* 從遠端儲存推送：`git push`

## .gitignore 配置
在把資料同步到github時，有時候會同步到一些不必要的檔案。
例如：環境設定( Eclipse的.metadata檔 )、編譯檔( java的.class檔 )等，可以利用.gitignore檔讓gitHub忽略這些檔案

## GIT 分支 (branch)
### 為什麼要用分支？

* 多人協作時，不可能都在 master
* 可以讓 master 都是正式版資料，可以開分支來做測試或開發，藉此不影響正式主機分支

### branch 介紹

* 分支就像是便利貼，貼在某個 commit 上
* 分支合併，主要是兩個 commit 進行合併

### 開分支流程

* 新增分支：`git branch 分支名稱`
* 查看分支：`git branch` 
* 切換分支：`git checkout 分支名稱`
* 刪除分支：`git branch -d 分支名稱 、-D 是強制刪除`
* 還原上個版本：`git reset HEAD^`

## Commit 介紹及使用
將暫存區的檔案提交到儲存庫儲存

        git commit -m "修改記錄"


## Git flow
Git flow 提出不同的分支功能，分別有 **master、develop 、hotfix、release、feature**五種分支。

而這五個分支，根據他們的性質，又有其他稱法：

* **長期分支** - `master` 分支、`develop` 分支

    原因：因 Master 與 Develop 分支會一直存活在整個 Git flow 裡，並不會被刪除掉。

* **短期分支** - `hotfix` 分支、`release` 分支、`feature` 分支

    原因：當完成專案後，這些更新的版本都會被合併進 Master 或 Develop 分支 ，之後就會被刪除掉。
    
### Master 分支
主要是用來放穩定、隨時可上線的版本。

### Develop 分支
這個分支主要是所有開發的基礎分支，當要新增功能的時候，所有的 Feature 分支都是從這個分支切出去的。

### Hotfix 分支
當線上產品發生緊急問題的時候，會從 Master 分支開一個 Hotfix 分支出來進行修復，Hotfix 分支修復完成之後，會合併回 Master 分支，也同時會合併一份到 Develop 分支。

### Release 分支
當認為 Develop 分支夠成熟了，就可以把 Develop 分支合併到 Release 分支，在這邊進行算是上線前的最後測試。

### Feature 分支
當要開始新增功能的時候，就是使用 Feature 分支的時候了。

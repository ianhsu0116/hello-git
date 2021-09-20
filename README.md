# 學習如何使用 git

---

# 下方為 git 筆記

# Unix (for MacOS, Linux user)

**\*註解：** Unix 是一種由 At&t 公司的 Bell Labs 發明出來的，是一種電腦作業系統(70 年代主流)，現在雖然沒人在用了，但在**MacOs, Linux**系統中 此功能就跟 **Windows 內的 CMD 一樣\***

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33c05f30-d400-4008-aff4-124d8af0abb7/_2021-05-19_4.43.14.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33c05f30-d400-4008-aff4-124d8af0abb7/_2021-05-19_4.43.14.png)

## Unix Commend

```jsx
// 一些常用的命令
**pwd: 顯示當前所在位置**

**cd: change directory 換到指定頁面（或資料夾內）**
ex. ****cd Desktop  // 到桌面

**Ls: list all files inside the directory

mkdir: 新增資料夾**
ex. mkdir project  // 在當前頁面新增一名為project的資料夾

**touch: 新增文件**
ex. touch index.html     // 在當前頁面新增index.html檔案

**cd ..: 退回上一個資料夾 ！cd及..中間的空白格是必要的

rm: remove files 移除當前資料夾的某文件**
ex. rm index.html

**rmdir**: **remove directory 移除資料夾**
ex. rmdir project //前提是移除前必須確定整個資料夾為空的 否則無法移除

**rm -rf: remove force強制移除資料夾，不管內部是否為空的**
ex. rm -rf project

**control + L : 清空當前頁面（非清除 只是騰出空間）

code files name: 直接在終端機內打開vscode並開好檔案，vscode的特殊功能
ex. code project // vscode會直接打開並開起內部所有文件**

// 以下示範在project內新增基本的html, css and js files
xuxiangyande-MacBook-Air:project ianian880116$ touch index.html
xuxiangyande-MacBook-Air:project ianian880116$ touch app.js
xuxiangyande-MacBook-Air:project ianian880116$ mkdir styles
xuxiangyande-MacBook-Air:project ianian880116$ cd styles
xuxiangyande-MacBook-Air:styles ianian880116$ touch style.scss
xuxiangyande-MacBook-Air:styles ianian880116$ cd ..

```

# 20210918 新增

```jsx
// 複製
**cp
ex. cp a.txt b.txt // 將a.txt複製並取名為b.txt

// 移動
mv

// 直接在終端機編輯檔案
nano
ex. nano test.txt

// 列出某file內的東西
cat
ex. cat test.txt

// 離開當前狀態
Q, control + c
ex. git config --list, git log的時候

// 在commit前，查看此次修改哪些code,比較working Dir 跟 Stuging Area的差異
git diff [file name]
ex. git diff test.txt

// 比較Stuging Area 跟 local Repo的差異
git diff --cached [file name]
ex. git diff --cached test.txt

// 查看所有commit 並且帶上修改了哪裡的細節
git log --stat

// add + commit 快捷方式 (只能用於 已commit過的file)
git commit -am "輸入commit敘述"

// 從Stuging Area 或是 local repo中移除
git restore --staged filename

// 反悔剛剛的修改 或是 回覆不小心刪除的檔案
git restore filename

// 假設不小心刪除了test, 如果是有用git的形況下，可以用這個復原 (要在add前才能回復，add之後就ggㄌ)
git restore test.txt

// 去到各個不同的commit 用git log可以看各個版本的版號
git checkout <版本號(輸入前幾碼即可)>

// 轉換不同的branch (原本是checkout 新版的會用switch)
git switch login

// 列出全部檔案
ls

// 列出全部檔案（列出隱藏檔）
ls -a

// 以完整格式列出檔案
ls -l

// 以完整格式列出所有的檔案
ls -al

// h -> 指的是humam, 指的是顯示人看得懂的東西
ls -alh  // 此會把檔案大小換成MB, KB ,G.....**

```

---

# Gti, GitHub

## Git commend

**_註解：_**

**Work Directory:** 是自己電腦的資料夾

**Local Repository: 又稱 Repo,** 類似共用資料夾的存在，同一個 team 的人員都會將編輯好的 code 上傳到此

**Staging Area:** 是一個當我們要將資料丟入 LR 時，會為了確保大家的版本一致，會先將資料放入此地方，接著在用 commit 丟入 LR 的時候會同時確認版本，若是版本不符就自動更新

(add→ 資料進入 Staging Area→commit→ 檢查版本更新沒問題後丟入 LR)

**Cloud Repository: 又稱 Remote,** 類似雲端資料夾(GitHub), 編輯好的檔案就會上傳到 GitHub

### 常用的 Git Commends

```jsx
**git init**
Initialized empty Git repository，創造一個隱藏的git資料夾，用來追蹤此資料夾內的所有改變
用 comand + shift + . 來顯示隱藏的files

**git config --global user.name "Ian Hsu"
git config --global user.email"ianian@fakemail.com"**
configuration, 設定作者跟信箱是為了讓主管或是同事知道這個code是誰寫的，以免找不倒人

**git config --list**
查詢有沒有成功設定name, email的地方

**git status**
查詢當前狀態，哪些檔案沒有add或是沒被commit，以及哪些有

**git add**
將指定的檔案放入Staging Area等待commit
ex. git add index.html / git add app.js

**git add** .
將當前資料夾內所有檔案丟入Staging Area

**git add** *.放檔案類型
將當前資料夾內所有**同一檔案類型**丟入Staging Area
ex. git add *.html

**git commit -m "add some code into iandx.html"**
將當前資料夾所有檔案commit並丟入LR，""內可以輸入一些註解，解釋你做了啥更動

**git rm --cached ""**
從Staging Area內移除某資料，cached是暫存的意思

// 補充 每當將code編輯結束過後，都需再將檔案 add 以及 commit一次！

**git log**
查詢歷史，會顯示先前被commit過的所有次數，及每次的 時間,作者,email

**.gitignore**
假設不想讓file內的log.txt文件在 add . 的時候被加入Staging Area內的話
先file內新增檔名為.gitignore的文件，接著在文件內輸入log.txt。
這樣即可避免log.txt被add
```

## branch, checkout and merge

**_註解：若都沒設定，一開始是在 master 上。可以設定其他分支(branch)來讓各個組員能分開編輯同一文件的不同部分_**

**_一個資料夾內可以有很多不同分支，每個分之內都可以有自己的文件，假設兩分支內同的文件也可以各自有自己的 code(寫完後再合併)，_**

```jsx
**git branch    創建一個分支**
創建一個叫 login 的branch => git branch login

**git ckeckout 移動到某分支**
移動到 login branch => git ckeckout login

**git merge 將某分支合併到master**
假設目前在master，將login和master合併 => git merge login
注意！ 合併前必須先add . / commit
若是login 和 master中的code 原先重疊的部分被更動了，會出現conflict, 需解決後才能commit
出現conflict: 回到code內去即可選擇解決辦法
**補充！： 解決完conflict後 還需要再add and commit一次！！！！！**
合併後就會將login的內容加入master內，但login的內容還是會單獨保存下來，checkout login即可看見
```

### **補充！： 解決完 conflict 後 還需要再 add and commit 一次！！！！！**

## Git push

**_註解：將編輯好的檔案從 Local Repo 丟入 GutHub_**

### 方法一

```jsx
在電腦中先做出資料夾及文件後，git init => add => commit => Local Repo，再使用
**git remote add origin https://github.com/ianian880116/project001.git**
將其連結到github的雲端資料夾， 接著再用
**git push -u origin master**
將masters內的所有data丟入remote（github）內
```

### 方法二 (better way)

```jsx
先在GitHub新建雲端資料夾後，在桌面的 終端機輸入
**git clone https://github.com/ianian880116/project002.git**
即可將GitHub的整個資料夾複製下來本地
接著再對文件進行編輯完成後 add => commit => Local Repo 再使用
**git push https://github.com/ianian880116/project002.git**
將編輯完後的文件丟回去GitHub

如此一來省下了幫文件initialize的步驟
**clone： 將網址內的所有檔案下載（複製）下來
註解： what does --set upstream do**
https://stackoverflow.com/questions/18031946/what-does-set-upstream-do
```

## Git pull

```jsx

要從雲端上拿取最新版本的文件時 可以這樣使用
假設雲端上有同事更新的最新版的文件後
可以在當前文件的資料夾內使用 **gut pull 此處放檔案所在的網址
ex. git pull https://github.com/ianian880116/project001.git**
即可將資料更新成最新版本
```

# 20210918 新增

現在 push, pull 已經無法用 account, password 認證了，需要用專屬的 token 認證

詳細資訊：[https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)

# 20210919 新增

## git flow

- 實際開發規則
  - 原則上，絕對不會在 main/master, develop branch 去 push, 一定是用別的 branch 去 merge 進去
  - 假設某功能會開發一陣子，那就會定時將 dev 的最新版本 merge 到我當前在開發的這個版本，這樣直到我最後功能做完，要將功能 merge 進去 dev 時，才不會有太多 conflict

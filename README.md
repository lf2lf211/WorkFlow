# git flow vs github flow vs gitlab flow
本文即將介紹三種最被廣泛使用的WorkFlow(工作流程)


* Git flow
* Github flow
* Gitlab flow



## Git flow<br>
先來介紹Git flow，他是最早誕生也是最早被廣泛使用的工作流程。<br>
它的特點是專案中會有兩個長期存在的分支，且絕對不會被刪除。分別為主分支**Master**以及開發分支**Develop**。
主分支用於存放對外發布的版本，在這裡的版本都是穩定的版本；而開發分支則是存放最新的開發版本。<br>

再來，還會有三種短期(臨時性)分支。都是開發完被merge進develop或master就會被刪除的分支。<br><br>

* 功能分支（feature branch）
* 修復分支（hotfix branch）
* 預發分支（release branch）

<br><br>

**一、主分支Master**<br><br>

首先，代碼庫會有一個且只有一個主分支。所有正式上線的版本，都是使用主分支版本。<br>
Git主分支的名字，默認叫做Master。專案一開起就會自動建立，版本庫初始化以後，默認在主分支進行開發。<br>
由於主分支要保持軟體穩定運行，主分支只用來發布重要版本，平時的開發版本則應該在另一條分支上進行，直到開發進展到可以發布程度才會與主分支合併。<br><br>

![](https://imgur.com/rw5NlMY.png)<br><br>

**二、開發分支Develop**<br><br>
此分支用來存放最新開發版本的代碼，是開發過程中代碼中心分支。如要正式對外發布則對主分支merge。<br>
以develop分支為起點新建feature分支，在feature 分支中進行新功能的開發或者代碼的修正，在合併回Develop分支。<br>
develop分支維會持續成為開發過程工的最新代碼，以便開發人員創建feature分支進行自己的工作。<br><br>

![](https://imgur.com/CSSYqJz.png)<br><br>
在默認情況下，Git 的merge為（fast-farward merge），會直接將Master分支指向Develop分支。<br>
而如果使用--no-ff參數merge，則會執行正常合併，在Master分支上生成一个新節點。這是為了保證版本History的清晰。<br>

* 默認情況<br>
![](https://imgur.com/nALludX.png)<br>
* 使用--no-ff參數<br>
![](https://imgur.com/FUG9L1a.png)<br>

**三、功能分支feature**<br><br>
功能分支的名字，通常用feature-\*的形式命名。<br>
為了某工功能而開發的分支，從Develop分支拉出來當feature分支，開發完成後要再併入Develop分支。是開發者直接更改代碼發送提交的分支。<br>


* feature branch示意圖<br>
![](https://imgur.com/O6E22LL.jpg)<br>
**四、修復分支hotfix**<br><br>
hotfix分支的名字通常用fixbug-\*的形式命名。<br>
hotfix分支是從Master分支分出來的，Master分支分支發布以後如有bug需要修復，這時就需要創建一個分支進行bug修復，修復結束後再合併進Master和Develop分支，最後删除hotfix分支。<br>



* hotfix branch示意圖<br>
![](https://imgur.com/CYHQiTX.jpg)<br>

**五、預發分支release**<br><br>
release分支的名字通常用release-\*的形式命名。<br>
release分支是指合并到Master分支之前，需要進行版本測試而產生出來的分支。<br>
在release分支裡，只處理與發布前相關的提交，該分支絕對不能包含需求變更或者功能變更等重大修正。<br>
release分支是從Develop分支分出來的，在預發布結束以後，必須合併進Develop和Master分支，最後刪除release分支。<br>


* Git Flow 示意圖<br>
![](https://imgur.com/yjhAIgK.jpg)<br>




## GitHub Flow<br>


建議使用Github Flow的情況 <br>
適合15-20人左右團隊，在部署上自動化且一天之類需要多次部署的開發。
<br><br><br>

github比git有多兩個服務，一個是fork，另一個是pull request（簡稱PR），還新增issue tracking用法;
先有一個共有的遠端倉庫(remote repository)，然後各自用fork把遠端倉庫fork回到自己的倉庫。開發好後，再利用PR回去共有的遠端倉庫，審核過後merge進master。
* 示意圖 <br>
![](https://imgur.com/uDjn6I1.png)<br>


整個 GitHub Flow 是基於分支，它是 Git 的一個核心概念。最主要就是令master 分支時常保持可以部署的狀態。進行新的作業時要從master 分支創建新的分支，分支命名應該具有描述性（如 userInfo、getAllUser......等等），讓其他人清楚知道分支正在進行的工作項目。<br>

在branch已經準備merging時，創建Pull Request，以Pull Request 進行交流，確認作業完成後與master分支進行合併，合併的代碼一定要測試
與master分支合併後，立刻部署。<br>

* 從master分支拉出新分支,修改且提交(Commits)<br><br>
分支建立後，開始進行修改。無論新增、修改或刪除檔案，都會提交更新並將它們加入分支。該過程可以使你追蹤分支的工作進度。<br>
提交動作也會產生工作記錄，讓其他開發者可以了解你做了些什麼。每個提交都要有相關的提交訊息(Commits Message)，解釋此次提交內容。另外，這樣也使每個提交都是一個個體，使我們在找到錯誤時可以恢復修改。<br>
* 發起Pull Request<br><br>
使任何人都能清楚看到，什麼樣的提交內容將會被合併（Merge）。在開發過程中都可以發起一個 Pull Request，像是：當你卡住了，需要幫助或是建議時；當你準備好讓某人來檢閱你的工作項目時。在 Pull Request 的訊息中使用 @ 來請求人以及團隊的反饋。<br>

* 發起Pull Request 後，檢閱人或團隊可以提出問題或是意見。也許是代碼不符合規範，或是有更好寫法，又或者是一切都良好。Pull Request 鼓勵這類型的討論。<br><br>

* 在討論及回饋中，如果有進需要進修改的內容，在分支中修正它並繼續推送修改。GitHub 會在 Pull Request 頁面顯示新提交以及新的回饋。<br><br>

* 在團隊檢核過提交內容後,就可以開始進行合併以及部屬。合併後，Pull Request 保存了當時的修改歷史記錄以及回饋。可以讓任開發人回頭檢視當初情況。<br><br>


### issue tracking <br><br>

![](https://imgur.com/pPOHqDm.png)<br>

開發時，可以給專案標記issue，還有其他不同標籤，還優化專案。當提交的時候，如果提交訊息中有fix #1 等，可以自動對應到相關編號的issue。<br>


## GitLab Flow
Git flow的優點是清晰可控，缺點是相對複雜，且需要頻繁切換分支。如果在版本快速迭代的專案中，是幾乎用不到Hotfix 和 Release 分支的，因為合併到master後如果有bug就直接修復且發布下個版本了，如果還使用這兩個分支，需要合併回develop 和 master分支，但實際上開發者很常忘記合併回這兩個主分支。

GitHub flow則適合項目是"持續發布"類型，缺點是，由於master為最新代碼，但是準被發布版本不一定是用最新代碼，或是有固定時間才發布更新的項目，就會有影響(例如:發布ios，時會審核master時，但審核期間如果有新版本推上會造成審核延遲)。如果只有一個master主分支就會不夠用。所以還得另外再建一個新分支來維護。<br>


所以又發展出了Gitlab flow，Gitlab flow 是 Git flow 与 Github flow 的综合。結合了兩者的優點，有開發環境上的彈性又有單一主分支的方便。
master分支的分支不夠，于是增加了一個 prodution 分支，專門用來發布版本。<br>

Gitlab flow 分成兩種情況來應付不同的開發流程<br><br>
* 持續發布
* 版本發布<br><br>

如果為持續發布的專案，建議在多出一個分支，為預發分支pre-production<br>

![](https://imgur.com/kZhnx7M.png)<br>

* 上游優先 Upstream First<br>

Gitlab flow 的最主要原則叫做"上游優先"（upsteam first）:只存在一个主分支master，此分支是所有其他分支的上游。所以分支合併的順序很重要，要一次和並且確保通過測試才可以往下游合併，除非是緊急情況，才允許跳過上游直接在下游操作合併。<br>

在**持續發布**(Environment Branches & Upstream First)中

每個環境(如開發環境,預發環境,測試環境...等)都會有對應的分支。如下圖，開發環境為master分支，預發環境為pre-production分支,生產環境為production
![](https://imgur.com/5lCbmgm.png)<br>


由上圖來舉例，如果生產環境(production)發生錯誤，則要建一個新分支修改完後合併到最上游的開發分支(master)，且經過測試，再繼續往預發分支合併(pre-production)，童要經過測試沒問題後才能夠在往下合併到生產環境。<br>

在**版本發布**(Release Branches & Upstream First)中



在 GitLab Flow中，對於版本發布的項目，建議每一個穩定的版本都要從master分支拉出來創建一個新分支，比如下圖的2-3-stable、2-4-stable(release分支)。<br>
根據對應的release分支分支在創建一個修復分支，修補bug後，一樣要照著上游優先規則，先合併到master分支，確認沒問題過後，才能夠合併到release分支，並且要更新版本號。<br>

![](https://imgur.com/TzfGyYH.png)<br>








参考链接：
<a href="http://www.ruanyifeng.com/blog/2012/07/git.html">阮一峰-Git分支管理策略</a>、<a href="http://www.ruanyifeng.com/blog/2015/12/git-workflow.html">阮一峰- Git 工作流程</a>、
<a href="https://medium.com/@trylovetom/%E8%AE%93%E6%88%91%E5%80%91%E4%BE%86%E4%BA%86%E8%A7%A3-github-flow-%E5%90%A7-4144caf1f1bf">MrGG-讓我們來了解 GitHub Flow 吧！</a>、<a href="https://drprincess.github.io/2017/12/26/Git%E4%B8%89%E5%A4%A7%E7%89%B9%E8%89%B2%E4%B9%8BWorkFlow(%E5%B7%A5%E4%BD%9C%E6%B5%81)/">DRPrincess-Git三大特色之WorkFlow(工作流)</a>

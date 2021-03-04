# Development Rules



## Backend
1. 開發須嚴格管理 `node` 版本，目前一律採用 `nvm` 作為 `node` 版本管理，必確實檢查每次開發皆是在對的 `node` 版本上開發。
2. 開發須嚴格管理套件版本，目前一律先採用 `yarn` 以及其 `yarn.lock` 作為套件版本管理工具。
    * 請熟悉並瞭解 `yarn` 所有使用規則與細節。
    * 請常常清空 `node_modules/` 並重新安裝套件，確認套件相容性是確實穩定的。
3. 務必確保 config files 保持一致，如 `dev.json` / `dev-cron.json` / `prod.json` / `dev-cron.json` 須一致。


## Pull Request
1. 發 PR 前，務必確實做完以下檢查，方能送出 PR。若有違反將直接 close 該次 PR 不進行審查。
    * Code 不包含任何 sensitive information （例如開發用的 id 、開發用假資料）
    * Code 不包含任何 useless / sensitive comment lines，僅能留下具有特意輔助說明功能的 comment lines
2. 發 PR 前，請確保所有 commits messages 內容都具有一定的資訊量，若發現有 garbage commits 請先用 `git rebase` 在 local 修改完 commits 再重新發 PR。若有違反將直接 close 該次 PR 不進行審查。commit messages 請把握以下原則：
    * 若有 新增/修改/移除 檔案/資料夾/function/class/...... 等，請敘述行為與對應的內容，例如 `remove useless text.json file` `add new class Cleaner in api.js file`，越詳細越好。追求「3 年後回來看 code 能從 commit message 清楚理解究竟做了什麼樣的處理」，讓 debug 時 traceback 更為方便有效。
    * 避免在一個 commit 塞入過多動作與 message，請在 commit 前確實整理開發過程與思緒，再下 commit。因此建議若在開發時可以先下假的 commit，等開發到一定程度後，再退回最初 commit，重新好好下正式的 commit，最後再利用 `git push -f` 來將假的 commit 覆蓋過去，最後才去發 PR。
    * 常見的 garbage commits message 如下： `fix` / `small fix` / `fix bug` / `fix bug 0` /`20191011` / `remove` / `refactor` / `add new file` / `add new function` / `test` / `tmp` 等
3. 發 PR 時，PR title 請直接以 branch name 為 title (注意務必和 branch name 一模一樣，未來 debug 好 traceback)，若有違反將直接 close 該次 PR 不進行審查。PR description 則摘取重要 commits message 即可，若想額外補充更好！越詳細完整越好！
4. PR 是開發的動脈，要保持清晰完整的內容，嚴謹以待 ><


## 進版
1. 前後端須完整重現從頭 build 到運作的過程後，確認皆無誤，方能進行進版。
    * 前端須清空 repo -> 拉下 repo -> 確認所有工具版本 -> 重新安裝套件 -> build static files
    * 後端須清空 repo -> 拉下 repo -> 確認所有工具版本 -> 重新安裝套件 -> 設定好 config files -> start server
2. 務必更新以下內容
    * README.md 內對應的版本、工具版本、部署步驟與其他注意事項等等
    * 若有 `package.json` 者，務必更新其中的版本
3. 進版後經過測試完畢，則進行「定版」動作，並打上 tag 與其對應的更新內容，一經「定版」，則不做任何修改，若遇到嚴重影響營運或是運作的 bugs，則直接「退版」。

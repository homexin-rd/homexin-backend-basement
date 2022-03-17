# Rules for GitHub Collaboration



## Branch
1. Handle one thing which meets up with your branch name as possible as you can. Do not be greedy to perform too many yet irrelevant tasks in one single branch; otherwise, the tracking would be killing in the coming future.
2. Branch names must be in the form of `[tag]/[name]`. Particularly,
    * `tag` is one of `feature`, `update`, `refactor`, and `fix`.
    * Use `-` for `name` (e.g., `careTaker-accept-order`).
3. Some examples of branch names:
    * `feature/get-admin-info`
    * `update/clear-hospitalAdmin-old-data`
    * `fix/get-careTaker-with-wrong-param`


## Commit Messages
1. Commit messages are important interface to tell others your motivation and what you add/update/remove.
2. Commit messages must be written in an explicit, plain, and clear manner. Commit messages must be written in COMPLETE SENTENCES; do not leave some short but imcomplete keywords. Compact and clear is the best; long yet clear is always better than short yet unclear.
3. Commite messages must be in the form of `[action]: [statements]`. Particularly,
    * `action` is one of `add`, `update`, `remove`, `refactor`, and `fix`.
    * `statements` must be complete and grammatically correct sentences.
4. Some examples of commit messages:
    * `add: Since we kick off developing with test cases, we add new files ./api/admin/test.js and ./api/admin/test2.js.`
    * `refactor: As a regular routine for refactoring work, we re-arrange APIs in ./api/admin/careTaker with no modification on thier functionality.`
    * `fix: Due to some typos in file ./api/admin/careTaker/careTaker.js, API /api/careTaker/profile/get malfunctions. We fix it by fixing all typos.`
    
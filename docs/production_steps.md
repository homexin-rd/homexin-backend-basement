# Upgrade Version in Production Steps



## Upgrade in Production
1. Merge codes into Master Branch (for both backend repo & warehouse repo).
2. Upgrade config warehouse version on both `homexin-prod` and `homexin-prod-cron` servers.
3. Check the `node`, `npm` and `yarn` versions on both `homexin-prod` and `homexin-prod-cron` servers.
4. Pull to upgrade the production version on both `homexin-prod` and `homexin-prod-cron` servers.
5. Clean up `node_modules/` and reinstall all packages `$ yarn install` on both `homexin-prod` and `homexin-prod-cron` servers.
6. Postpone pm2 process on `homexin-prod-cron` machine while restart pm2 process on `homexin-prod` servver.
7. Ensure all process work well on `homexin-prod` server, and then restart process on `homexin-prod-cron` server and check it.
8. Save pm2 process `$ pm2 save` (c.f. `backend/README.md`)


## Follow-up TODO
1. Open new a Swagger version.
2. Write a draft for the release for both backend repo & warehouse repo.
3. Update versions pinned on Slack.
4. Test / Hotfix.
5. Confirm production version: tag and release for both backend repo & warehouse repo.
7. Clean unused branches for both backend repo & warehouse repo.


## Hot-fix Steps
1. Create a new hot-fix branch from `master` branch and develop hot fixes on it.
2. Open a Pull Request for merging the hot-fix branch to `master` branch.
3. Open a Pull Request for merging the `master` branch to `develop` branch to guarantee a conflict-free development.
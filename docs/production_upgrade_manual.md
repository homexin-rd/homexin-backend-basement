# Production Version Upgrade Manual



## Upgrade in Production
1. Merge codes into Master Branch (for backend repo & warehouse repos).
2. Upgrade config warehouse (i.e., `homexin-backend-configuration`) version on both `homexin-prod` and `homexin-prod-cron` servers.
2. Upgrade static data warehouse (i.e., `homexin-backend-static-data`) version on both `homexin-prod` and `homexin-prod-cron` servers.
3. Start services by running docker containers (refer to `README.md` in each repo).



## Follow-ups to the Upgrade
1. Update/sync files in the `homexin-backend-postman` repo (e.g., GraphQL schema file and errorCode file).
2. Write drafts for the release for backend repo & warehouse repos.
3. Update versions pinned on Slack.
4. Announce the upgrade in Slack channels.
5. Test / Hotfix.
6. Confirm production version: tag and release for backend repo & warehouse repos.
7. Clean merged/unused branches of backend repo & warehouse repos.


## How to Handle a Hot-fix?
1. Create a new hot-fix branch from `master` branch and develop hot fixes on it.
2. Open a Pull Request for merging the hot-fix branch to `master` branch.
3. Open a Pull Request for merging the `master` branch to `develop` branch to guarantee a conflict-free process.
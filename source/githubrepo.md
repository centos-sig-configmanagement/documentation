# Github project settings


This page describes the configuration needed to setup the communication between
[ci.centos.org](https://ci.centos.org) and github.

## WebHooks

For more details, see the [CentOS wiki](https://wiki.centos.org/QaWiki/CI/GithubIntegration).

1. Open the project settings

    ![Settings button](images/github-settings.png)

1. Select Webhooks

    ![Webhook menu button](images/github-webhooks.png)

1. Click "Add a webhook" button

    ![Webhook add button](images/github-webhooks-add.png)

1. Create a push webhook to the url `https://ci.centos.org/github-webhook/`

    ![Webhook for the Github plugin](images/github-webhooks-gh.png)

1. Click "Add a webhook" button

    ![Webhook add button](images/github-webhooks-add.png)

1. Create a push webhook to the url `https://ci.centos.org/ghprbhook/`

    * select 'Let me select individual events'
    * unselect 'Push' and select 'Pull Request' and 'Issue Comment'

    ![Webhook for the Github Pull Request Builder plugin](images/github-webhooks-ghprb.png)

1. Check that the webhooks are correctly configured (green)

    ![Webhook status](images/github-webhooks-ok.png)


## Protected branches

When we have a stable repo, we can enforce ci testing by using the following
steps:

1. Open the project settings

    ![Settings button](images/github-settings.png)

1. Select Webhooks

    ![Webhook menu button](images/github-branch-menu.png)

1. Select the branch you want to protect

    ![Webhook menu button](images/github-protected-branch-select.png)

1. Select "Protect this Branch", "Require status checks to pass before merging",
    *unselect* "Require branches to be up to date before merging", and select
    "ci.centos.org". If you do not see "ci.centos.org", it means that there has not
    yet been any pull requests tests on the repo.

    ![Webhook menu button](images/github-protected-branch.png)


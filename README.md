# useful-one-liners
Terminal commands/pipes/mini-scripts I always have to search for :/

## Github clone all my repositories

`gh repo list OWNER --limit 1000 | awk '{print $1; }' | xargs -L1 gh repo clone`

Assumes `gh` is installed.

## Heroku CLI add repository to existing app

`heroku git:remote -a example-app`

<https://devcenter.heroku.com/articles/git#for-an-existing-app>

# Deployment

## API

<aside class="notice">This section is dedictated to deploying the Democrasales API.</aside>

### Staging Instructions:

Heroku instructions link: [https://devcenter.heroku.com/articles/git](https://devcenter.heroku.com/articles/git)

```shell
# Setup Heroku Git Remote
heroku git:remote -a democrasales-api-staging

git remote rename heroku staging
```   

Deployment Setup Instructions:

  * Setup git remote:
    * `heroku git:remote -a democrasales-api-staging`
  * Rename remote to staging
    * `git remote rename heroku staging`

```shell
# Staging Deployment Commands
git push staging staging:master

heroku run rake db:migrate --remote production

heroku restart --remote staging
```       

Deployment Instructions (Follow these in order when deploying):

  * Deploying staging branch to staging
    * `git push staging staging:master`
  * Run Migrations:
    * `heroku run rake db:migrate --remote staging`
  * Restart server:
    * `heroku restart --remote staging`


### Production Instructions:

Heroku instructions link: [https://devcenter.heroku.com/articles/git](https://devcenter.heroku.com/articles/git)

```shell
# Setup Heroku Git Remote
heroku git:remote -a democrasales-api-production

git remote rename heroku production
```

Deployment Setup Instructions:

  * Setup git remote:
    * `heroku git:remote -a democrasales-api-production`
  * Rename remote to production
    * `git remote rename heroku production`

```shell
# Production Deployment Commands
git push production master

heroku run rake db:migrate --remote production

heroku restart --remote production
```       

Deployment Instructions (Follow these in order when deploying):

  * Deploying production branch to production
    * `git push production master`
  * Run Migrations:
    * `heroku run rake db:migrate --remote production`
  * Restart server:
    * `heroku restart --remote production`

## Web

<aside class="notice">This section is dedictated to deploying the Democrasales Web App.</aside>

### Staging Instructions:

Heroku instructions link: [https://devcenter.heroku.com/articles/git](https://devcenter.heroku.com/articles/git)

```shell
# Setup Heroku Git Remote
heroku git:remote -a democrasales-web-staging

git remote rename heroku staging
```   

Deployment Setup Instructions:

  * Setup git remote:
    * `heroku git:remote -a democrasales-web-staging`
  * Rename remote to staging
    * `git remote rename heroku staging`

```shell
# Staging Deployment Commands
git push staging staging:master

heroku restart --remote staging
```       

Deployment Instructions (Follow these in order when deploying):

  * Deploying staging branch to staging
    * `git push staging staging:master`
  * Restart server:
    * `heroku restart --remote staging`


### Production Instructions:

Heroku instructions link: [https://devcenter.heroku.com/articles/git](https://devcenter.heroku.com/articles/git)

```shell
# Setup Heroku Git Remote
heroku git:remote -a democrasales-web-production

git remote rename heroku production
```

Deployment Setup Instructions:

  * Setup git remote:
    * `heroku git:remote -a democrasales-web-production`
  * Rename remote to production
    * `git remote rename heroku production`

```shell
# Production Deployment Commands
git push production master


heroku restart --remote production
```       

Deployment Instructions (Follow these in order when deploying):

  * Deploying production branch to production
    * `git push production master`
  * Restart server:
    * `heroku restart --remote production`

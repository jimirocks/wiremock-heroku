# wiremock-heroku
A simple way to deploy [WireMock](http://www.wiremock.org) on to Heroku

## Prerequisites
- [Heroku account](https://signup.heroku.com)
- [Heroku toolbelt installed](https://toolbelt.heroku.com)

## Instructions

### TLDR:
    git clone git@github.com:jimirocks/wiremock-heroku.git && \
    cd wiremock-heroku && \
    ./wiremock-heroku.sh <unique_app_name>

### For those who want to understand:
- Clone this repository
```
git clone git@github.com:jimirocks/wiremock-heroku.git
cd wiremock-heroku
```
- Add a heroku remote
```
heroku create <unique_app_name>
```
- Add the [Energized Work](http://www.energizedwork.com) downloadable jar buildpack
```
heroku config:set 'NO_PRE_DEPLOY=true'
heroku buildpacks:set https://github.com/energizedwork/heroku-buildpack-runnable-jar
```
- Start the app
```
git push heroku master
```
- Check it
```
curl http://<unique_app_name>.herokuapp.com/__admin/mappings/new \
-d '{ "request": { "url": "/", "method": "GET" }, "response": { "body": "This is WireMock running on Heroku\n" }}'
curl http://<unique_app_name>.herokuapp.com/
```

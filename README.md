# humhub-docker-compose
Humhub via docker-compose
forked from myoshimi/humhub-docker-compose


====

# Usage

There is a ways to launch docker containers using Humhub development version from github repository.

## Github version

* ```git clone``` from the repository
* Download github repository of [Humhub](https://humhub.org/en/download)

``` shell
git clone https://github.com/tomofu74/humhub-docker-compose
cd humhub-docker-compose
git clone https://github.com/humhub/humhub
cd humhub
chmod 777 -R assets
chmod 777 -R protected/config
chmod 777 -R protected/modules
chmod 777 -R protected/runtime
chmod 777 -R uploads
cd ..
docker-compose -f docker-compose-dev.yml build
docker-compose -f docker-compose-dev.yml up -d
```

You can access elgg web service after stopping ```composer``` container.

# Non-volatile Volume

* Directory ```Volumes/db``` is mounted for mariadb container
* ```humhub``` is mounted for app container

# Humhub Install

Access 'localhost:80' with your browser. Installer is start.
Then, db settings are host: db , dbname : humhub , username : humhub, password : password

# humhub-docker-compose
Humhub via docker-compose
forked from myoshimi/humhub-docker-compose


====

# Usage

There are two ways to launch docker containers. First uses "Release
version" of Humhub. Second uses Humhub development version from github
repository.

As the repository does not include the codes of Humhub itself,
you need to fetch from official web site or github repository.

## Release version

* ```git clone``` from the repository
* Download latest version of [Humhub](https://humhub.org/en/download)
  community edition
* Decompress them to ```humhub-docker-compose/humhub``` directory

``` shell
git clone https://github.com/myoshimi/humhub-docker-compose
cd humhub-docker-compose
mkdir humhub
tar xzvf <Download Directory>/humhub-1.3.17.tar.gz \
  -C <path to humhub-docker-compose>/humhub --strip=1
```

* run docker-compose-rel.yml
  * ```php/Dockerfile.rel`` is built for humhub-app container

``` shell
docker-compose -f docker-compose-rel.yml build
docker-compose -f docker-compose-rel.yml up -d
```

## Github version

* ```git clone``` from the repository
* Download github repository of [Humhub](https://humhub.org/en/download)

``` shell
git clone https://github.com/tomofu74/humhub-docker-compose
cd humhub-docker-compose
git clone https://github.com/humhub/humhub
docker-compose -f docker-compose-dev.yml build
docker-compose -f docker-compose-dev.yml up -d
cd humhub
chmod 777 -R assets
chmod 777 -R protected/config
chmod 777 -R protected/modules
chmod 777 -R protected/runtime
chmod 777 -R uploads
composer global require "fxp/composer-asset-plugin:~1.4.2"
composer install
```

You can access elgg web service after stopping ```composer``` container.

# Non-volatile Volume

* Directory ```Volumes/db``` is mounted for mariadb container
* ```humhub``` is mounted for app container


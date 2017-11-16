# Laravel 5.5 Development Image

Docker image for local development with [Laravel 5.5](http://laravel.com) projects, based on the official [PHP 7](http://hub.docker.com/_/php/) image. 

Find it on [Dockerhub](https://hub.docker.com/r/winternight/docker-laravel-dev/builds/).

`$ docker pull winternight/docker-laravel-dev:latest`

## Motivation

I use [zeit.co](https://zeit.co) and [hyper.sh](https://hyper.sh) for dev deployments that need to be accessible to clients. For Laravel-based applications, a Docker image is necessary since [hyper.sh](https://hyper.sh) is made specifically for Docker and [zeit.co](https://zeit.co)only natively support NodeJS.

I'm not a fan of huge containers that bundle Apache, PHP, MySQL and other applications into one but I also do not want a complicated multi-container setup for a development-stage deployment because of the associated cost.

## Description

This is a docker image for an all-purpose PHPFPM (PHP Version 7.2) container.  It is based on the `7.1-cli-alpine` tag of the [official PHP Docker image](https://hub.docker.com/_/php/). [Patch version](http://semver.org) upgrades are thus done automatically on build (e.g. `7.1.x` to `7.1.y`) but for minor version upgrades (e.g. `7.1.x` to `7.2.x`), a new Dockerfile should be created and tagged appropriately.

## New and Removed Features

There are some new features and deprecated parts in PHP 7.2 that made changes to the Dockerfile necessary:

* `mcrypt` has been [deprecated in 7.1 and removed in 7.2](http://php.net/manual/en/migration71.deprecated.php) in favor of OpenSSL
* `xdebug` is not yet supported with PHP 7.2 -- I will move the image to PHP 7.2 as soon as the final version is released

## Extensions

The installed extensions are enough for local development of [Laravel 5.5 projects](https://laravel.com).

## Building

In order to build this image yourself, simply run the following command:

`$ docker build -t winternight/docker-laravel-dev:latest .`

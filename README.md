Play Auth Slick Seed Template
=====================================

This is a fork of the official Silhouette Seed project. If you want to have a first look at Silhouette, I suggest you have a look at the [official project](https://github.com/mohiva/play-silhouette-seed).


## Example

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

(The "Build App" phase will take a few minutes)

Or you can find a running example of this template under the following URL: https://play-silhouette-seed.herokuapp.com/

## Features

* Sign Up
* Sign In (Credentials)
* Change Password
* Edit Profile
* Social Auth (Facebook, Google+, VK, Twitter, Xing, Yahoo)
* Two-factor authentication with Clef
* Dependency Injection with Guice
* Publishing Events
* Avatar service
* Remember me functionality
* [Security headers](https://www.playframework.com/documentation/2.4.x/SecurityHeaders)
* [CSRF Protection](https://www.playframework.com/documentation/2.4.x/ScalaCsrf)
* play-slick database access


## Documentation

Consulate the [Silhouette documentation](http://silhouette.mohiva.com/docs) for more information. If you need help with the integration of Silhouette into your project, don't hesitate and ask questions in our [mailing list](https://groups.google.com/forum/#!forum/play-silhouette) or on [Stack Overflow](http://stackoverflow.com/questions/tagged/playframework).

### Slick

The template stores all authentication information in a database via [Slick](http://slick.typesafe.com/) It uses an [PostgreSQL](http://www.postgresql.org/) database by default.

In order to use another database supported by Slick, you need to change the driver in your application.conf and add the corresponding JDBC driver to your dependencies. The [Play Slick documentation](https://www.playframework.com/documentation/2.4.x/PlaySlick) has more information about database configuration.

### Database Init
You need to create these database tables first:

CREATE TABLE "user" (
	"userID" VARCHAR NOT NULL PRIMARY KEY,
	"email" VARCHAR,
	"fullName" VARCHAR,
	"age" INTEGER,
	"sex" VARCHAR,
	"avatarURL" VARCHAR
);

CREATE TABLE "logininfo" (
	"id" SERIAL NOT NULL PRIMARY KEY,
	"providerID" VARCHAR NOT NULL,
	"providerKey" VARCHAR NOT NULL
);

CREATE TABLE "userlogininfo" (
	"userID" VARCHAR NOT NULL,
	"loginInfoId" BIGINT NOT NULL
);

CREATE TABLE "passwordinfo" (
	"hasher" VARCHAR NOT NULL,
	"password" VARCHAR NOT NULL,
	"salt" VARCHAR,
	"loginInfoId" BIGINT NOT NULL
);

CREATE TABLE "oauth1info" (
	"id" SERIAL NOT NULL PRIMARY KEY,
	"token" VARCHAR NOT NULL,
	"secret" VARCHAR NOT NULL,
	"loginInfoId" BIGINT NOT NULL
);

CREATE TABLE "oauth2info" (
	"id" SERIAL NOT NULL PRIMARY KEY,
	"accesstoken" VARCHAR NOT NULL,
	"tokentype" VARCHAR,
	"expiresin" INTEGER,
	"refreshtoken" VARCHAR,
	"logininfoid" BIGINT NOT NULL
);

CREATE TABLE "openidinfo" (
	"id" VARCHAR NOT NULL PRIMARY KEY,
	"logininfoid" BIGINT NOT NULL
);

CREATE TABLE "openidattributes" (
	"id" VARCHAR NOT NULL,
	"key" VARCHAR NOT NULL,
	"value" VARCHAR NOT NULL
);

# License

The code is licensed under [Apache License v2.0](http://www.apache.org/licenses/LICENSE-2.0).

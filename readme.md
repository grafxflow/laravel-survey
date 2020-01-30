Laravel survey
==============

Custom survey app in laravel.

Pre-requisites
==============

- Linux
- Node.js v7+
- MySQL v5.5+ (or MariaDB)
- PHP v5.6+

Building
========

Inside the repo's folder.

Install Node.js dependencies, it will take some time.

```
$ npm i
```

Download [composer][composer-url].

```
$ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
$ php composer-setup.php
```

Install [composer][composer-url]'s dependencies.

```
$ php composer.phar install
```

Copy and edit your own `.env` file out of `.env.example`, it is essential.

```
$ cp .env.example .env
```

Generate the new `APP_KEY` value on the `.env` file.

```
$ php artisan key:generate
```

You'll have to configure MySQL yourself, it's not that hard.

```
Log into your MySQL as root.

Say your .env file has the following confs

  DB_USERNAME=laravel_survey_user
  DB_HOST=127.0.0.1
  DB_PASSWORD=laravel_survey_pass
  DB_DATABASE=laravel_survey_database

Create the user DB_USERNAME at DB_HOST identified by DB_PASSWORD.
> CREATE USER laravel_survey_user@127.0.0.1 IDENTIFIED BY 'laravel_survey_pass';

Create the database DB_DATABASE.
> CREATE DATABASE laravel_survey_database;

Grant DB_USERNAME all privileges to DB_DATABASE.
> GRANT ALL ON laravel_survey_database.* TO laravel_survey_user@127.0.0.1;
```

Execute laravel's migrations.

```
$ php artisan migrate
```

Run webpack's tasks to generate JavaScript and CSS assets.

```
$ npm run dev
OR
$ npm run production # to generate minified files
```

Start up the server.

```
$ php artisan serve
```

> You will have to access `http://localhost:8000/laravel/`.

Optional 3rd party integrations
===============================

I recommend you just updating the `.env` file variables `PUSHER_ENABLED=true` and `GOOGLE_RECAPTCHA_ENABLED=true` and starting up the server. The first page will tell you about missing configurations in these optional 3rd party integrations. A form will be created for input and validation of the credentials. If some error occur you'll be notified. In case all credentials are correct the `.env` file will be updated and you'll be able to proceed normally.

# Pusher

Create your app at [pusher's dashboard][pusher-url]. Edit the `.env` file with your credentials

```
PUSHER_ENABLED=true
PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_APP_CLUSTER=
```

# Google Recaptcha

Go to [Google Recaptcha's admin page][google-recaptcha-url] and register a new site. Edit the `.env` file with your keys

```
GOOGLE_RECAPTCHA_ENABLED=true
GOOGLE_RECAPTCHA_SITE_SECRET=
GOOGLE_RECAPTCHA_SITE_KEY=
```

License
=======

[MIT][LICENSE]

[google-recaptcha-url]: https://www.google.com/recaptcha/admin#list
[pusher-url]: https://dashboard.pusher.com/accounts/sign_in
[composer-url]: https://getcomposer.org/
[LICENSE]: LICENSE


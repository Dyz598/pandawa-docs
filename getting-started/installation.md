# Installation/Setup

1. To install git clone the `pandawa-skeleton` project with
the desirable project name.

```
git clone https://github.com/pandawa/pandawa-skeleton.git example-app
```

2. Go to the project directory and remove the `.git` folder and initialize
a new git repository if necessary.

```
rm -rf .git

git init
```

3. Composer install, setup environment and generate Laravel app key.

```
composer install

cp .env.example .env

php artisan key:generate
```

And Done! We are ready to start to create our Pandawa application. Go through
the documentation or the [Basics/Sample App](basics.md) tutorial to familiarize 
yourself with Pandawa by creating a sample application.
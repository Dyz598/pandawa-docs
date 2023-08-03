# Installation/Setup

1. To start using Pandawa run the following composer `create-project` command with
the desirable project name.

```
composer create-project pandawa/skeleton:dev-master example-app
```

2. Initialize repository if necessary.

```
git init
```

3. Setup environment the same way you would in Laravel and generate application
key using the `php artisan key:generate` command.

```
cp .env.example .env

php artisan key:generate
```

And Done! We are ready to start to create our Pandawa application. Go through
the documentation or the [Basics/Sample App](basics.md) tutorial to familiarize 
yourself with Pandawa by creating a sample application.
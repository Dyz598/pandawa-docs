Pandawa has separated Laravel's default service providers to make
its base skeleton more plain and so by default it does not have much features yet.

So we need to instruct/install all the components we need for our application.
For example if our application needs a database we would install the `database-bundle`
and if we don't we wouldn't install it.

For example if our application needs a database we would install the `database-bundle`
and if we don't we wouldn't install it.

`Bundles` are similar to Service Providers in Laravel they are responsible for
registering parts of our code to the application. In order to instruct it to register
exactly what parts of our code to the application we use plugins
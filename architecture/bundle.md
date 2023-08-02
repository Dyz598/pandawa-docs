# Bundles

Bundles are the essence of Pandawa's architecture to achieve features such as modularity in your code. 
They have similar functionality with [Laravel's Service Provider](https://laravel.com/docs/providers) to
register parts of your code to configure your application.

Bundles are basically classes that are used collect parts of your code such as **routes**, **services** and
**event listeners** and register/bootstrap them to the application.

Pandawa has removed Laravel's default service providers to make its base skeleton more plain and so by 
default it does not have much features yet. We separated these default service providers and made them
into Bundles which are listed and can be searched here https://github.com/pandawa.

So everytime in our Pandawa application we need to install all the components/bundles we need
for our application. For example if our application needs a database we would install the `pandawa/database-bundle`
 package.

**NOTE:** You can still use Laravel service providers in Pandawa so if you want to install
packages/dependencies made by the community or Laravel itself it should still work just fine but
you have to install the component/bundle it depends on.

### Basics

A simple `Bundle` class would look like something like the following.

```php
<?php

declare(strict_types=1);

namespace App;

use Pandawa\Component\Foundation\Bundle\Bundle;

/**
 * @author  Aldi Arief <aldiarief598@gmail.com>
 */
class SampleBundle extends Bundle
{
}
```

Its a class typically named by the Domain or Functionality or Vendor Name suffixed with the word `Bundle` and
extends the `Pandawa\Component\Foundation\Bundle\Bundle` class. 

For example if you want to add code to connect your application to Kafka you would typically make a `KafkaBundle` 
class and have the Bundle register and configure all your Kafka code to your application.

### Plugins
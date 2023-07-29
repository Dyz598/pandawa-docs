# The Basics/Sample App

In this example app we will be making one `GET` method API with
the endpoint `ping` that will return a JSON response with the
field `pong` with the boolean value `true`.

In Pandawa most of your code will be placed/done in the `src` folder.

Pandawa has separated Laravel's default service providers to make
its base skeleton more plain and so by default it does not have 
features/components yet. So we need to instruct/install all 
the components we need for our application.

For this example we will be installing the following bundles/packages from
the following commands to install the things we need for our application.

```
composer require pandawa/routing-bundle:"^5.0"

composer require pandawa/annotation-bundle:"^5.0"

composer require pandawa/routing-annotations:"^5.0"

composer require pandawa/view-bundle:"^5.0"
```

These four packages will install the routing, view and annotation component/feature to 
the application.

Create a `SampleBundle` class that extends the `Bundle` class
from Pandawa in the `src` folder.

```php
<?php

declare(strict_types=1);

namespace App;

use Pandawa\Bundle\RoutingBundle\Plugin\ImportRouteAnnotationPlugin;
use Pandawa\Component\Foundation\Bundle\Bundle;
use Pandawa\Contracts\Foundation\HasPluginInterface;

/**
 * @author  Aldi Arief <aldiarief598@gmail.com>
 */
class SampleBundle extends Bundle implements HasPluginInterface
{
    public function plugins(): array
    {
        return [
            ImportRouteAnnotationPlugin::class,
        ];
    }
}
```

The class above will register parts of our code to the application.
We implement the `HasPluginInterface` if we have specific parts of 
our code to be registered. The `ImportRouteAnnotationPlugin` will instruct 
to specifically register routes from classes that have the route annotation which will be
explained soon.

Register the class/bundle above by putting it in the `config/bundles.php` array
which would look like something like the following.


```php
<?php

return [
    App\SampleBundle::class,
];
```

Now we will create the Ping API.

Create the `Http/Controller` directory and create a `SampleController` class 
which would look like something like this.

Directory:
```
.
├── bootstrap
├── config
├── public
├── src/
│   ├── Http/
│   │   └── Controller/
│   │       └── SampleController.php
│   └── SampleBundle.php
├── storage
├── tests
└── vendor
```

Class:
```php
<?php

declare(strict_types=1);

namespace App\Http\Controller;

use Illuminate\Http\JsonResponse;
use Illuminate\Routing\Controller;
use Pandawa\Annotations\Routing\Routable;
use Pandawa\Annotations\Routing\Route;

/**
 * @author  Aldi Arief <aldiarief598@gmail.com>
 */
#[Routable]
class SampleController extends Controller
{
    #[Route(uri: 'ping', methods: 'GET')]
    public function ping(): JsonResponse
    {
        return response()->json(['pong' => true]);
    }
}
```

In the `SampleController` class above we instruct the bundle using the `ImportRouteAnnotationPlugin`
to register all class using the `Routable` PHP attribute or `annotation` we call it here and
register routes for the methods that use the `Route` attribute/annotation.

Run the Pandawa application same like Laravel with the following command.

```
php artisan serve
```

Test the API using tools like Postman and you should get the following json response.

```json
{
    "pong": true
}
```

And Done! We have successfully created our first sample application. This should give you
an idea how Pandawa works. For the next steps go through the rest of the documentation
to familiarize more with Pandawa's architecture and its features to create the application
you need.

#Learn how to create bundle
Migrate a service from src to bundle\
Extract the service class and move it to it's own location\
Create a lib directory \
Create the bundle directory KnpUIpsum and src folder\
Modify the namespace KnpU\LoremIpsum\
Edit composer Autoloader 
```
   "autoload": {
        "psr-4": {
            "KnpU\\LoremIpsumBundle\\":"lib/LoremIpsumBundle/src/",
            "App\\": "src/"
        }
    }
```
Run ```compser dump-autolod``` command to tell composer to load \

Edit service.yml to register the service\

```
 KnpU\LoremIpsumBundle\KnpUIpsum: ~
```
Library vs Bundle - Bundle provide services
Create a class that will extend Bundle class that use Symfony\Component\HttpKernel\Bundle\Bundle\
Open bundle.php and configure bundle for all environments
```
KnpU\LoremIpsumBundle\KnpULoremIpsumBunde::class => ['all' => true]
```
To load dependency and services create into the src folder a new folder Dependency injection
Create a class KnpULoremIpsumExtension that extend extension and implement the Load method
Add a resources\config directory
Add a service.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<container xmlns="http://symfony.com/schema/dic/services"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://symfony.com/schema/dic/services
        https://symfony.com/schema/dic/services/services-1.0.xsd">

    <services>
        <service id="knpu_lorem_ipsum.knpu_ipsum" class="KnpU\LoremIpsumBundle\KnpUIpsum" public="true"/>
        <service id="KnpU\LoremIpsumBundle\KnpUIpsum" alias="knpu_lorem_ipsum.knpu_ipsum" public="false"/>
    </services>
</container>

```
edit loader method from DependencyInjection to load xml file
Create yaml config file in packages




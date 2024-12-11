# setup:di:compile errors

## Cannot instantiate interface

```console
Cannot instantiate interface <Namespace>\<Module>\Api\<Interface>
```

1. Make sure the re is a preference for the interface in `di.xml`
2. Run `rm -rf generated/code/* var/tmp/* var/cache/*` and try again

##  Class `<class>` generation error

```console                                                                                                                                                                             
Class <class> generation error: The requested class did not generate properly, because the 'generated' directory permission is read-on  
ly. If --- after running the 'bin/magento setup:di:compile' CLI command when the 'generated' directory permission is set to write --- the requested class did not generate  
properly, then you must add the generated class object to the signature of the related construct method, only.                                                                                                                                                                                                               
```

Composer packages have likely changed. Run `composer install` or `composer update` and try again

## syntax error, unexpected ')', expecting variable (T_VARIABLE)#0 /data/web/magento2/vendor/composer/ClassLoader.php(427): Composer\Autoload\{closure}()

```console
syntax error, unexpected ')', expecting variable (T_VARIABLE)#0 /data/web/magento2/vendor/composer/ClassLoader.php(427): Composer\Autoload\{closure}()
#1 [internal function]: Composer\Autoload\ClassLoader->loadClass()
#2 [internal function]: spl_autoload_call()
#3 /data/web/magento2/setup/src/Magento/Setup/Module/Di/Code/Reader/ClassesScanner.php(134): class_exists()
#4 /data/web/magento2/setup/src/Magento/Setup/Module/Di/Code/Reader/ClassesScanner.php(117): Magento\Setup\Module\Di\Code\Reader\ClassesScanner->includeClass()
#5 /data/web/magento2/setup/src/Magento/Setup/Module/Di/Code/Reader/ClassesScanner.php(87): Magento\Setup\Module\Di\Code\Reader\ClassesScanner->extract()
#6 /data/web/magento2/setup/src/Magento/Setup/Module/Di/App/Task/Operation/RepositoryGenerator.php(61): Magento\Setup\Module\Di\Code\Reader\ClassesScanner->getList()
#7 /data/web/magento2/setup/src/Magento/Setup/Module/Di/App/Task/Manager.php(56): Magento\Setup\Module\Di\App\Task\Operation\RepositoryGenerator->doOperation()
#8 /data/web/magento2/setup/src/Magento/Setup/Console/Command/DiCompileCommand.php(216): Magento\Setup\Module\Di\App\Task\Manager->process()
#9 /data/web/magento2/vendor/symfony/console/Command/Command.php(255): Magento\Setup\Console\Command\DiCompileCommand->execute()
#10 /data/web/magento2/vendor/symfony/console/Application.php(1009): Symfony\Component\Console\Command\Command->run()
#11 /data/web/magento2/vendor/symfony/console/Application.php(273): Symfony\Component\Console\Application->doRunCommand()
#12 /data/web/magento2/vendor/magento/framework/Console/Cli.php(115): Symfony\Component\Console\Application->doRun()
#13 /data/web/magento2/vendor/symfony/console/Application.php(149): Magento\Framework\Console\Cli->doRun()
#14 /data/web/magento2/bin/magento(23): Symfony\Component\Console\Application->run()
#15 {main}
```

In `\Composer\Autoload\ClassLoader::loadClass` add `echo var_export($class, true) . PHP_EOL;` to see which class is causing the error, debug the class from here

## Interface "Magento\Framework\ObjectManager\ResetAfterRequestInterface" not found

```console
Interface "Magento\Framework\ObjectManager\ResetAfterRequestInterface" not found#0 /data/web/magento2/vendor/composer/ClassLoader.php(579): include()
#1 /data/web/magento2/vendor/composer/ClassLoader.php(429): Composer\Autoload\{closure}()
#2 [internal function]: Composer\Autoload\ClassLoader->loadClass()
#3 /data/web/magento2/vendor/magento/framework/ObjectManager/Relations/Runtime.php(38): class_exists()
#4 /data/web/magento2/vendor/magento/framework/Interception/Config/Config.php(157): Magento\Framework\ObjectManager\Relations\Runtime->has()
#5 /data/web/magento2/vendor/magento/framework/Interception/Config/Config.php(180): Magento\Framework\Interception\Config\Config->_inheritInterception()
#6 /data/web/magento2/vendor/magento/framework/Interception/Config/Config.php(213): Magento\Framework\Interception\Config\Config->hasPlugins()
#7 /data/web/magento2/vendor/magento/framework/Interception/Config/Config.php(190): Magento\Framework\Interception\Config\Config->generateIntercepted()
#8 /data/web/magento2/vendor/magento/framework/Interception/Config/Config.php(122): Magento\Framework\Interception\Config\Config->initializeUncompiled()
#9 /data/web/magento2/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php(121): Magento\Framework\Interception\Config\Config->__construct()
#10 /data/web/magento2/vendor/magento/framework/ObjectManager/Factory/Dynamic/Developer.php(66): Magento\Framework\ObjectManager\Factory\AbstractFactory->createObject()
#11 /data/web/magento2/vendor/magento/framework/ObjectManager/ObjectManager.php(70): Magento\Framework\ObjectManager\Factory\Dynamic\Developer->create()
#12 /data/web/magento2/vendor/magento/framework/App/ObjectManager/Environment/Developer.php(84): Magento\Framework\ObjectManager\ObjectManager->get()
#13 /data/web/magento2/vendor/magento/framework/App/ObjectManagerFactory.php(191): Magento\Framework\App\ObjectManager\Environment\Developer->configureObjectManager()
#14 /data/web/magento2/vendor/magento/framework/App/Bootstrap.php(212): Magento\Framework\App\ObjectManagerFactory->create()
#15 /data/web/magento2/vendor/magento/framework/App/Bootstrap.php(127): Magento\Framework\App\Bootstrap->__construct()
#16 /data/web/magento2/vendor/magento/framework/Console/Cli.php(184): Magento\Framework\App\Bootstrap::create()
#17 /data/web/magento2/vendor/magento/framework/Console/Cli.php(84): Magento\Framework\Console\Cli->initObjectManager()
#18 /data/web/magento2/bin/magento(22): Magento\Framework\Console\Cli->__construct()
#19 {main}
```

Some modules, for example `magento/module-re-captcha-version-3-invisible` version `2.0.4` requires this class (`Magento\Framework\ObjectManager\ResetAfterRequestInterface`), while version `2.0.2` does not.

Search the `vendor` directory for modules that require this interface and downgrade them to a version that does not require it (add the correct version to `composer.json` and run `composer install`)

If you have a older `composer.lock` file that works, check for the correct versions there.
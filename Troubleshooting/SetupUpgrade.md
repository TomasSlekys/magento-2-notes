# setup:upgrade errors

## call_user_func() parameter error

```console
Warning: call_user_func() expects parameter 1 to be a valid callback, class '<vendor>\<module>\Setup\Patch\Data\<class>' not found in /var/www/html/vendor/magento/framework/Setup/Patch/PatchRegistry.php on line 141
```

Check namespace of `'<vendor>\<module>\Setup\Patch\Data\<class>'`

## Class `<CLASS>` not found

```console
Class '<CLASS>' not found #0 /var/www/html/vendor/magento/framework/ObjectManager/Factory/Compiled.php(108): Magento\Framework\ObjectManager\Factory\AbstractFactory->createObject('CreationLabs\\Du...', Array)
```

Run `bin/magento s:d:c` first, then try `bin/magento s:up` again

## [Docker] SQL permission error to create triggers

1. Change the 'user' in `app/etc/env.php` to `root`
2. Run `bin/magento s:up` again
3. Change the 'user' back to the original user

## Autoload error 

```console
Autoload error: We can't read some files that are required to run the Magento application. This usually means file permissions are set incorrectly.
```

1. Delete the `vendor` folder
2. Run `composer install`
3. Run `bin/magento s:up` again
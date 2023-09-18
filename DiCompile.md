# setup:di:compile errors

## Cannot instantiate interface

```console
Cannot instantiate interface <Namespace>\<Module>\Api\<Interface>
```

Run `rm -rf generated/code/* var/tmp/* var/cache/*` and try again

##  Class `<class>` generation error

```console                                                                                                                                                                             
Class <class> generation error: The requested class did not generate properly, because the 'generated' directory permission is read-on  
ly. If --- after running the 'bin/magento setup:di:compile' CLI command when the 'generated' directory permission is set to write --- the requested class did not generate  
properly, then you must add the generated class object to the signature of the related construct method, only.                                                                                                                                                                                                               
```

Composer packages have likely changed. Run `composer install` or `composer update` and try again
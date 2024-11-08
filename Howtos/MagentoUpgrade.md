# Magento 2 Upgrade

## Useful links

- [Magento 2 Released Versions](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions)
- [Magento 2 Upgrade Guide](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade)

## How to upgrade Magento 2

### 1. Switch to maintenance mode to prevent access to your store during the upgrade process.

```console
bin/magento maintenance:enable
```

### 2. Install composer-root-update-plugin if not already installed.

This helps to update the root `composer.json` file when upgrading Magento 2.

```console
composer require magento/composer-root-update-plugin ~2.0 --no-update
composer update 
```

Full usage instructions can be found in `vendor/magento/composer-root-update-plugin/README.md`

### 3. Disable cron jobs

Starting the upgrade process while asynchronous processes, such as message queue consumers, are running may cause data corruption. 
To prevent data corruption, disable all cron jobs.

```conosle 
bin/magento cron:remove
```

### 4. Start all message queue consumers manually to ensure that all messages are consumed.

```console
bin/magento cron:run --group=consumers
```

Wait for the cron job to complete. You can monitor the status of the job with a process viewer or by running the `ps aux | grep 'bin/magento queue'` command multiple times until all processes complete.

### 5. Create a backup of the composer.json file.

```console
cp composer.json composer.json.bak
```

### 6. Upgrade your instance using the composer require-commerce command

```console
composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
```

For example:

```console
composer require-commerce magento/product-community-edition 2.4.7-p3 --no-update
```

Command options include:

`<product>` - (Required) The package to upgrade. For on-premises installations, this value must be either product-community-edition or product-enterprise-edition.

`<version>` - (Required) The version of Adobe Commerce that you are upgrading to. For example, 2.4.3.

`--no-update` - (Required) Disables the automatic update of the dependencies.

`--interactive-root-conflicts` - (Optional) Allows you to interactively view and update any out-of-date values from previous versions, or any customized values that do not match the version you are upgrading to.

`--force-root-updates` - (Optional) Overrides all conflicting custom values with the expected Commerce values.

`--help` - (Optional) Provides usage details about the plugin.

If neither `--interactive-root-conflicts` nor `--force-root-updates` are specified, the command keeps the existing values that are in conflict and displays a warning message. To learn more about the plugin, refer to the Plugin Usage README.

### 7. Update the dependencies.

```console
composer update
```
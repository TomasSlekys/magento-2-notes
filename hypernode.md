# Hypernode

## Enable HTTPS

```
hmv <name>.hypernode.io --https --force-https
```

## Point /data/web/public to pub folder

Rename `public` folder to `magento2` and create a symlink to pub folder

```
mv public/ magento2
ln -s magento2/pub/ public
```

Result

```
lrwxrwxrwx  1 app app   13 Oct  9 06:19 public -> magento2/pub/
```
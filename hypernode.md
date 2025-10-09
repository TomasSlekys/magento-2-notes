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

## Enable HTTP Auth

Add HTTP Auth user

```
htpasswd -c /data/web/htpasswd dev
```

Uncomment lines in `nginx/<name>.hypernode.io/server.basicauth.conf`

```
auth_basic           "Login required";
auth_basic_user_file /data/web/htpasswd;
```
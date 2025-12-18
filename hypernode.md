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

## Add alternate store

Add store "newstore" to example.hypernode.io

```
hmv newstore.example.hypernode.io --webroot /data/web/public
```

Create `server.storecode` file inside `nginx/newstore.example.hypernode.io`

```
touch ~/nginx/newstore.example.hypernode.io/server.storecode
```

Add store code to file

```
nano ~/nginx/newstore.example.hypernode.io/server.storecode
```

If website - use website code

```
set $storecode "newstore_website_code";
set $storetype "website";
```

If store - use store code

```
set $storecode "newstore_store_code";
set $storetype "store";
```

Add https

```
hmv newstore.example.hypernode.io --https --force-https
```
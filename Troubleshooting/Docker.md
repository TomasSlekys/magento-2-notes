# Docker Troubleshooting

## Could not find an available, non-overlapping IPv4 address pool error 

Running `docker-compose up` gives the following error:

```console
ERROR: could not find an available, non-overlapping IPv4 address pool among the defaults to assign to the network
```

This happens when the default docker network address pool is exhausted (you have too many docker networks created).

Either delete some of the networks or prune all networks with the following command:

```console
docker network prune
```

## Network not found error

Running `docker-compose up` gives the following error:

```console
... docker cannot start service ... network not found ...
```

This happens for example if you prune your docker networks.

Run `docker-compose up --force-recreate` to recreate the containers including the network
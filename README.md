# mongodb-replicaset-docker

The connection string to access this single-node MongoDB replica set is:

```
mongodb://127.0.0.1:27017/?replicaSet=rs0
```

If you have error - getaddrinfo ENOTFOUND host.docker.internal

You need to change host

Firstly connect to DB
```
mongosh "mongodb://127.0.0.1:27017"
```

Then change config
```
cfg = rs.conf()
cfg.members[0].host = "localhost:27017" // or "127.0.0.1:27017"
rs.reconfig(cfg, { force: true })
```

Exit the shell
```
exit
```

And now you can test to connect
```
mongosh "mongodb://127.0.0.1:27017/?replicaSet=rs0"
```
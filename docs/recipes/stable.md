# Spin up a stable version

First up, in the best case scenario where you want to run DHIS2 2.32.0 on
an empty database, you are able to run:

```bash
d2 cluster up 2.32.0

# result
# ---
# channel: stable
# dhis2Version: 2.32.0
# dbVersion: empty
```

Usually you want to `seed` your database with a database dump from
Sierra Leone to have an instance set up with data. If you add the
`--seed` command to the command above, it will try to find the database
dump 2.32.0 in the
[dhis2-db-demo](https://github.com/dhis2/dhis2-demo-db/tree/master/sierra-leone)
repo. That doesn't exist, but 2.32 does.

```bash
d2 cluster up 2.32.0 --seed
# fail: there's no db dump with 2.32.0

d2 cluster up 2.32.0 --db-version 2.32 --seed

# result
# ---
# channel: stable
# dhis2Version: 2.32.0
# dbVersion: 2.32
```

# Spin up a development version

Let's switch to the **dev** channel as we want the bleeding edge build
from 2.32. We want it seeded with a 2.32 dump so we are going to run it
with `--seed`.

```bash
d2 cluster up 2.32 --channel dev --seed

# result
# ---
# channel: dev
# dhis2Version: 2.32
# dbVersion: 2.32
```

Since the 2.32 branch exists in
[dhis2-core](https://github.com/dhis2/dhis2-core/tree/2.32) and the 2.32
dump exists in
[dhis2-demo-db](https://github.com/dhis2/dhis2-demo-db/tree/master/sierra-leone/2.32)
the tool doesn't need more information to create an environment.

Now, let's run a `master` build from the **dev** channel:

```bash
d2 cluster up master \
    --channel dev \
    --db-version dev \
    --seed

# result
# ---
# channel: dev
# dhis2Version: master
# dbVersion: dev
```

Since the `--dhis2-version` argument was omitted, it used the `{name}`
as fallback. Since we used `master` as the name, and the `master` tag
exists in the
[dhis2/core-dev](https://cloud.docker.com/u/dhis2/repository/docker/dhis2/core-dev/tags)
it is able to resolve a complete environment.

We could also have run:

```bash
d2 cluster up master \
    --channel dev \
    --db-version dev \
    --dhis2-version master \
    --seed
```

The name can be anything you wish, but remember to specify `channel`,
`dhis2-version`, and `db-version` in that case.

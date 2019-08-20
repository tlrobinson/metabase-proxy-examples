This runs a couple instances of Metabase using the code as it is on
your local filesystem. It needs:

* An image named `metabase-local`
* The `MB_ROOT` env var set to the path to your local MB repo

The following can help with setup:

```
# Add this function to your shell functions. It runs lein deps and
# saves the result as an image so that deps don't have to get
# downloaded every time
cache-lein() {
    imagename="$1"
    docker run -v $(pwd):/app pandeiro/lein deps
    docker commit $(docker ps -a | awk '/lein deps/ {print $1}' | head -1) "$imagename"
}

cd path/to/metabase
cache-lein metabase-local # Actually creates the image
export MB_ROOT=`pwd`
```

With that setup in place:

```
cd metabase-proxy-examples/caddy-load-balanced-local
docker-compose up
```

You can view the load-balanced instances at http://metabase-caddy.localhost:8888/

You can connect to instance REPL ports at `10000` and `10001`

Postgres details:

* username: postgres
* password: secretpassword
* port: 6432

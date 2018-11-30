Metabase Proxy Examples
=======================

Usage
-----

    cd EXAMPLE_NAME
    docker-compose up
    # open http://metabase-EXAMPLE_NAME.localhost/metabase in your browser

Examples
--------

* caddy: simple proxy from http://metabase-caddy.localhost/ to Metabase
* caddy-non-root-path: proxy from http://metabase-caddy-non-root-path.localhost/metabase to Metabase
* caddy-restricted: proxies full app on http://metabase-caddy-private.localhost/ with IP restrictions, and only public embeds on http://metabase-caddy-public.localhost/ with no restrictions
* caddy-force-language: forces http://metabase-caddy-force-language.localhost/ to always use a specific language

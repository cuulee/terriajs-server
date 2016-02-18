## TerriaJS-Server

This is a basic NodeJS Express server that serves up a (not included) static [TerriaJS](https://github.com/TerriaJS/TerriaJS)-based site (such as [National Map](http://nationalmap.gov.au)) with a few additional useful services:

* `/proxy`: a proxy service which applies CORS headers for data providers that lack them. Add URLs to config.json to enable them.
* `/proj4def`: a proj4 coordinate reference system lookup service.
* `/convert`: an ogr2ogr server-side conversion service.
* `/ping`: returns 200 OK.
* All other requests are served from the `wwwroot` directory you provide on the command line, which defaults to `./wwwroot`

### Stand-alone installation (without serving NationalMap)

#### Install

1. `git clone https://github.com/terriajs/terriajs-server`
2. `cd terriajs-server`
3. `npm install`

#### Configure

Create a local config.json with a list of domains you're willing to proxy for:

```json
{
    "proxyDomains": [
        "gov.au"
    ]
}
```

#### Run

1. `node app`

```
app [options] [path-to-wwwroot]

Options:
  --port                         Port to listen on.              [default: 3001]
  --public                       Run a public server that listens on all
                                 interfaces.           [boolean] [default: true]
  --upstream-proxy               A standard proxy server that will be used to
                                 retrieve data.  Specify a URL including port,
                                 e.g. "http://proxy:8000".
  --bypass-upstream-proxy-hosts  A comma separated list of hosts that will
                                 bypass the specified upstream_proxy, e.g.
                                 "lanhost1,lanhost2"
  --help, -h                     Show this help.                       [boolean]
  ```

#### Tests

1. Run `npm test`

### Installation with NationalMap

  Just [install NationalMap](https://github.com/NICTA/nationalmap/wiki/Deploying-a-copy-of-National-Map). TerriaJS-Server is installed to `node_modules/terriajs-server`, and you can run it manually as `node_modules/terriajs-server ./wwwroot`.


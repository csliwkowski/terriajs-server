## TerriaJS-Server

This is a basic NodeJS Express server that serves up a (not included) static [TerriaJS](https://github.com/TerriaJS/TerriaJS)-based site (such as [National Map](http://nationalmap.gov.au)) with a few additional useful services:

* `/proxy`: a proxy service which applies CORS headers for data providers that lack them. Add URLs to config.json to enable them.
* `/proj4def`: a proj4 coordinate reference system lookup service.
* `/convert`: an ogr2ogr server-side conversion service.
* `/proxyabledomains`: return a JSON of domains the server is willing to proxy for
* `/ping`: returns 200 OK.
* All other requests are served from the `wwwroot` directory you provide on the command line, which defaults to `./wwwroot`
* If files `[wwwroot]/404.html` and/or `[wwwroot]/500.html` exist, they will be served for those HTTP error codes.
* Services that require HTTP authentication can be proxied by adding credentials to a `proxyauth.json` file.

### Stand-alone installation (without serving NationalMap)

#### Install

1. `git clone https://github.com/terriajs/terriajs-server`
2. `cd terriajs-server`
3. `npm install`

#### Configure
 
Copy serverconfig.json.example to serverconfig.json and configure as needed. See comments inside that file.

#### Run

1. `npm start -- [options] [path/to/wwwroot]`

```
TerriaJS Server 2.0.0
lib/app.js [options] [path/to/wwwroot]

Options:
  --port             Port to listen on.                          [default: 3001]
  --public           Run a public server that listens on all interfaces.
                                                       [boolean] [default: true]
  --config-file      File containing settings such as allowed domains to proxy.
                     See serverconfig.json.example
  --proxy-auth-file  File containing auth information for proxied domains. See
                     proxyAuth.json.example
  --help, -h         Show this help.                                   [boolean]
```

To run the server in the foreground, you can do this:

`node . [arguments as above]`

#### Tests

1. Run `npm test`

### Installation with NationalMap

  Just [install NationalMap](https://github.com/NICTA/nationalmap/wiki/Deploying-a-copy-of-National-Map). TerriaJS-Server is installed to `node_modules/terriajs-server`, and you can run it manually as `node_modules/terriajs-server ./wwwroot`.


# ClanOfTheCloud.com Javascript client

**Important node: v3.0.0 breaks compatibility, see History below**

Before anything, you need to **register for free** on [ClanOfTheCloud.com](http://account.clanofthecloud.com).

The 'jsclient' can be used both from node.js or from a web browser. It's written in Coffee-script, then compiled to
javascript with Browserify and optionnally minified to a mere 20kB, less than 5kB after gzip compression.

Note: This client is not feature complete yet. It implements the latest [API](http://docs.clanofthecloud.apiary.io/#).
Feel free to submit bug reports and/or pull requests.

You can read more about concepts and data model on [API Wiki](https://github.com/clanofthecloud/api/wiki).

## Set up

After cloning this repository, you can use `npm install` to grab dependencies (with node.js installed).
Coffee-script sources live in `/src` while the compiled JS is in `/lib`.

`npm run build:browser` will compile the Coffee-script sources to `/lib/bundle.js` and `/lib/bundle.min.js`

`npm run build:node` builds the node version of the module.

## Use in a Web browser

You need a single JS script, `/lib/bundle.js`, which inlines `superagent`, the only dependency.

Then you can use the Clan class as a starting point. See [/lib/example.html](https://github.com/clanofthecloud/javascript-client/blob/master/lib/example.html)
for a basic example.

## Sample JS application

The sample app resides in `./sample`. You can use `npm install` to install an HTTP server to serve
the static assets, and `npm start` to start it.

Then browse to [http://127.0.0.1:8080](http://127.0.0.1:8080).

## History

- `2016/11/17` added :
	- `sendResetMailPassword` : if an account with email lost the password, it can be resetted with this method 
	- `loginWithShortCode` : a user having a shortcode from email can login with this method
	- `resumeSession`: prevouisly stored (gamer_id, gamer_secret) could be used to log again
	- `match.move`: param osn added (was supposed to be inside the `move` json in previous version), no change to do, just user the version you prefer. 
- `2016/10/28` v3.0.0 changed API to gamer vfs: you get exactly what you set (Set a json string, get a json string, not an object like in v2)
- `2016/06/10` added : game vfs, matches
- `2016/06/11` added : indexes
- `2016/06/13` added : kv store 
- `2016/06/15` fixed : superagent back to version 1.2.0 as 2.0.0 as double callbakc problems...
			 allowing to pass endpoint (sandbox, prod) at setup whitout changing the prefixer...

## TODO

- documentation for classes, usage, params and returned JSON... and errors too
- package client and server lib separately

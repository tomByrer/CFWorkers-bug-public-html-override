# CFWorkers-bug-public-html-override
demonstrates CloudFlare Workers's new feature of auto-importing HTML unintended incompatibility

Projects will break if one moves old code into a new project.  The new templates use `./public/index.html` as the base of responses, but old code still expects to write htm via `return new Response()` in the `index.js` file.  Took me an hour to find I had comment out config lines:

```js
// ./wrangler.json
// comment this out to have your index.js to return htm
	 "assets": {
	 	"binding": "ASSETS",
	 	"directory": "./public"
	 },
```
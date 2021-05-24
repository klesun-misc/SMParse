In this fork I added a `package.json` so that you could reference this repository as an npm dependency like this:
```json
{
  ...
  "dependencies": {
    "SMParse": "https://github.com/klesun-misc/SMParse/tarball/7738f570a599637d79858e951349eb9b0427779d"
  }
}
```
And then require it like this:
```javascript
const SMParse = require('SMParse/SMParse/res/js/parser.js');

const parsed = new SMParse(smDataStr);
console.log(parsed);
```
______________________________________________

# SMParse

A web-based parser for StepMania chart files.  Supports SM and SSC files.

## Web UI

Drag a chart file onto the page to load its tags and render the steps.

### Requirements

* [jCanvas](http://projects.calebevans.me/jcanvas/)

## Node.js module

The `SMParse` class is provided by [parser.js](SMParse/res/js/parser.js), which can be loaded independently:

```js
var SMParse = require("path/to/parser");
require("fs").readFile("path/to/chart.ssc", function(err, data) {
    var parse = new SMParse(data);
});
```

## Data structure

```
{
    meta: {title, subtitle, artist, credit, origin, cd, genre, type: [format, version], select},
    files: {banner, jacket, cd, disc, video, bg, music, lyrics},
    times: {offset, sample: {start, length}, labels},
    changes: {bpm, stop, delay, warp, timesig, tick, combo, speed, scroll, fake, key, attack, bg, fg},
    charts: [{name, credit, type, desc, style, diff, meter, data, radar, notes}],
    raw
}
```

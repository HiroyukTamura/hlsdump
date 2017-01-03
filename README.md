# hlsdump [![Build Status](https://travis-ci.org/uupaa/hlsdump.svg)](https://travis-ci.org/uupaa/hlsdump)

[![npm](https://nodei.co/npm/uupaa.hlsdump.svg?downloads=true&stars=true)](https://nodei.co/npm/uupaa.hlsdump/)

HLS recorder

This module made of [WebModule](https://github.com/uupaa/WebModule).

## Documentation
- [Spec](https://github.com/uupaa/hlsdump/wiki/)
- [API Spec](https://github.com/uupaa/hlsdump/wiki/)

## Browser, Node.js, NW.js and Electron

```js
<script src="<module-dir>/lib/WebModule.js"></script>
<script src="<module-dir>/lib/HLSDump.js"></script>

<input type="checkbox" id="m3u8" value="m3u8" checked />m3u8
<input type="checkbox" id="ts" value="ts" checked />ts
<input type="checkbox" id="aac" value="aac" checked />aac
<input type="checkbox" id="mp4" value="mp4" checked />mp4
<input type="checkbox" id="pcm" value="pcm" checked />pcm
<hr />
<input id="url" type="text" value="" placeholder="http://.../playlist.m3u8" style="width:40%" />
<input type="button" value="rec" onclick="__rec()" />
<input type="button" value="stop" onclick="__stop()" />

<script>

var rec = null;
function __rec() {
    var url = document.querySelector("#url").value || "";

    rec = new HLSDump(url, {
        autoStart:      false,
        dir:            "", // mkdir "test/el/{timestamp}/"
        bulkDuration:   1,
        readyCallback:  function() {
            rec.start();
        },
        m3u8:           !!document.querySelector("#m3u8").checked,
        ts:             !!document.querySelector("#ts").checked,
        aac:            !!document.querySelector("#aac").checked,
        mp4:            !!document.querySelector("#mp4").checked,
        pcm:            !!document.querySelector("#pcm").checked,
    });
}
function __stop() {
    if (rec) {
        rec.stop();
    }
}

</script>
```

## Node.js

```sh
node index.js --help        # usage
node index.js -d <output-dir> -m3u8 -ts -aac -mp4
```


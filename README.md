# player-sdk-js
Player SDK for online torrent streaming on your site

## Features
* Supports magnet-uri and external torrent-files
* Supports video (avi, mkv, mp4, m4v) with subtitles (vtt, srt)
* No additional plugins/extensions required

## Basic usage
```html
...
    <div id="player" class="webtor" />
    <script>
        window.webtor = window.webtor || [];
        window.webtor.push({
            id: 'player',
            magnet: 'magnet:?xt=urn:btih:08ada5a7a6183aae1e09d831df6748d566095a10&dn=Sintel&tr=udp%3A%2F%2Fexplodie.org%3A6969&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969&tr=udp%3A%2F%2Ftracker.empire-js.us%3A1337&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337&tr=wss%3A%2F%2Ftracker.btorrent.xyz&tr=wss%3A%2F%2Ftracker.fastcast.nz&tr=wss%3A%2F%2Ftracker.openwebtorrent.com&ws=https%3A%2F%2Fwebtorrent.io%2Ftorrents%2F',
            on: function(e) {
                if (e.name == window.webtor.TORRENT_FETCHED) {
                    console.log('Torrent fetched!')
                }
                if (e.name == window.webtor.TORRENT_ERROR) {
                    console.log('Torrent error!')
                }
            },
        });
    </script>
    <script src="https://cdn.jsdelivr.net/npm/@webtor/player-sdk-js/dist/index.min.js" charset="utf-8"></script>
...
```
[Here is live example](https://jsbin.com/cevugup/edit?html,output)

## Player configuration
Attribute  | Description
-----------|-------------
id         | Element id where player will be embedded
magnet     | Magnet-uri
torrentUrl | Url of the torrent-file (HTTP-server **MUST** include header "Access-Control-Allow-Origin: *" to allow torrent-file download on client-side )
theme      | Can be "light" or "dark". If not set theme will be selected automatically
on         | Callback-function to capture player events

## Player events
Name            | Description
----------------|-------------
TORRENT_FETCHED | Indicates that torrent has been loaded
TORRENT_ERROR   | Indicates if some error has occured during loading (timeout, wrong url, etc...)

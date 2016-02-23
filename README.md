# show-time

Watch episodes of your favorite TV shows with a simple CLI, using http://showrss.info

**Required: Node ≥ 4.0**

## Installation

```sh
npm install -g show-time
```

## Configuration

* Register at [ShowRSS](http://showrss.info) (just a login/password, no mail or real name)
* Configure your feed, just follow the steps on the website
* Run ``show-time --configure`` to initialize your configuration

## Usage

```sh
show-time
```

* Select your episode, subtitles, and enjoy :)

### Demo

![](https://github.com/naholyr/show-time/raw/master/screencast.gif)

### CLI options

```
  --version, -v    Show version and exit
  --help, -h       Show this help and exit
  --clear-cache    Clears cache and exit
  --configure      Configuration wizard
  --config <file>  Use alternative configuration file
  --cache <path>   Path to cache (--no-cache to disable)
  --player <name>  Automatically play to given player
  --feed <url>     ShowRSS feed URL
  --lang <lang>    Preferred language for subtitles

Valid players: chromecast, vlc, airplay, mplayer, smplayer, mphc, potplayer, mpv, omx, webplay, jack
```

### Known bugs

* Peerflix seems to not be working with node 5.x, using 4.x for now
* It happens castnow fails to start, I quit and restart a few seconds/minutes later and it works again

## How it works

* ``show-time`` grabs your RSS feed from showrss.info to show a list of recently available episodes
* It will then search on opensubtitles.org for subtitles (results cached for 1 hour)
* Once the torrent magnet and the subtitles grabbed, it runs ``peerflix`` to download and play video

## The cache

A lot of things are put in the cache, which is located at ``$HOME/.show-time/cache``:

* The downloaded torrents
* OpenSubtitles results (.json)
* Subtitles (.srt)

You can remove files manually, or you can empty the whole cache with ``show-time --clear-cache``

## Roadmap

* Add configuration options
* Add support for chromecast

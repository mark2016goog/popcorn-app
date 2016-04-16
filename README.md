合法视频服务如Netflix、亚马逊和Hulu的流行降低了消费者的BitTorrent文件共享服务的需求，但如今BitTorrent社区发起了反击，一群开发者推出了一款基于BitTorren的免费开源视频应用Popcorn Time，支持Windows、Mac和Linux，提供了一个没有广告界面清爽播放操作简单的高清视频点播服务，其中的电影多数都是720p或1080p格式。程序源代码托管在GitHub上，这意味着MPAA之类的版权机构很难将其扼杀在摇篮中。Popcorn Time利用BT种子服务YTS传 输流视频文件，使用OpenSubtitles提供不同语言的字幕。开发者Sebastian说，程序启动时会跳出免责对话框（如图所示），声明 Popcorn Time使用BitTorrent下载电影和做种，表示种子文件可能并不合法，他们不对此产生的问题负责。(via Solidot)


#Popcorn time [![Dependency Status](https://david-dm.org/popcorn-time/popcorn-app.png?theme=shields.io)](https://david-dm.org/popcorn-time/popcorn-time)

# [Goodbye](https://medium.com/p/93f890b8c9f4)
**Update** *15 March 2014* : Sorry friends, but we removed issue tracking because it was being used to link elsewhere.

## Idea

To allow any computer user to watch movies easily streaming from torrents, without any particular knowledge.

![Demo Screenshot](http://getpopcornti.me/images/how-ui.png)

### Status

Under development (RC1) for Mac OSX - Windows - Linux.
 
### APIs

**Currently used:**
- ~~[RottenTomatoes](http://developer.rottentomatoes.com) for movies metadata.~~
- ~~[PirateBay](http://thepiratebay.se/browse/207/0/7/0) Recent popular movies list.~~
- [YIFY](http://yts.re/api) movie torrents API.
- [OpenSubtitles](http://trac.opensubtitles.org/projects/opensubtitles/wiki/XMLRPC) for subtitles
- [TheMovieDB](http://www.themoviedb.org/) for movies metadata.

**In discussion:**
- [SubtitleSeeker](http://www.api.subtitleseeker.com/About/Api-Search/) for subtitles.


## Building

### Dependencies

You will need nodejs and grunt:

    $ npm install -g grunt-cli

### Build

Install the node modules:

    $ npm install

Build with:

    $ grunt nodewkbuild

By default it will build for your current platform however you can control that
by specifying a comma separated list of platforms in the `platforms` option to
grunt:

    $ grunt nodewkbuild --platforms=linux32,linux64,mac,win

You can also build for all platforms with:

    $ grunt nodewkbuild --platforms=all

## Any problem?

### Regarding superagent dependency
Due to [wrong browser verification](https://github.com/visionmedia/superagent/issues/95) on a dependency, this hard fix must be applied.
Replace `node_modules/moviedb/node_modules/superagent/index.js` contents with:
```javascript
// if (typeof window != 'undefined') {
//   module.exports = require('./lib/superagent');
// } else if (process.env.SUPERAGENT_COV) {
//   module.exports = require('./lib-cov/node');
// } else {
  module.exports = require('./lib/node');
// }
```

### Regarding Video, MP4 H264 Playback
- Info: https://github.com/rogerwang/node-webkit/wiki/Support-mp3-and-h264-in-video-and-audio-tag
- Needed to build a custom build of node-webkit that adds h264 support (or you can download ready-to-go builds from https://file.ac/s4Lt3Vo6rls/)
- Alternatively, we can replace a .so and .dll file from the correspondent Chrome build to node-webkit and node-webkit.exe


## Development
- Run `compass watch` in Terminal for CSS compiling and listen to future changes.
- [How to build with SublimeText](https://github.com/rogerwang/node-webkit/wiki/Debugging-with-Sublime-Text-2-and-3)
- Currently Gaze to watch all files and reload the app is disabled due to memory leaks and unstability.
- Run node-webkit from the root directory with --debug to enable debugging mode like so ```node-webkit . --debug```

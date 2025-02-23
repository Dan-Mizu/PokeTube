## SyncTube
Synchronized video viewing with chat and other features.
Lightweight modern implementation and very easy way to run locally.

Default channel example: https://synctube.onrender.com/

### Features
- Multi-Language support
- Hotkeys (`Alt-P` for global play/pause, [etc](https://github.com/RblSb/SyncTube/blob/d3f6d4e6434527569d13f211a0eb074c5a11992e/src/client/Buttons.hx#L303-L314))
- Mobile view with page fullscreen
- Way to play local videos for network users (without NAT loopback feature)
- Playback rate synchronization (with leader)
- `/30`, `/-21`, etc to rewind video playback in seconds
- Links mask: `foo.com/bar${1-4}.mp4` to add multiple items
- Override every front-end file you want (`user/res` folder)
- [Native mobile client](https://github.com/RblSb/SyncTubeApp)

### Supported players
- Youtube (videos, shorts, streams and playlists)
- [Streamable](https://streamable.com)
- [VK](https://vk.com/video)
- Raw mp4 videos and m3u8 playlists (or any other media format supported in browser)
- Iframes (without sync)

### Setup
- Open `4200` port in your router settings (port is customizable)
- `npm ci` in this project folder ([NodeJS 14+](https://nodejs.org) required)
- Run `node build/server.js`
- Open showed "Local" link for yourself and send "Global" link to friends

### Setup (Docker)
As alternative, you can install Docker and run:
> ```shell
> docker build -t synctube .
> docker run --rm -it -p 4200:4200 -v ${PWD}/user:/usr/src/app/user synctube
> ```

or

> ```shell
> docker compose up -d
> ```

- (Docker container hides real local/global ips, so you need to checkout it manually)


### Optional dependencies
If you want to enable `Cache on server` feature for Youtube player, you can also run:
```shell
npm i @distube/ytdl-core@latest
```
And install `ffmpeg` on your server system. Default cache size is 3.0 GiB.

### Configuration
It's just works, but you can also check [user/ folder](/user/README.md) for server settings and additional customization.

### Plugins
- [octosubs](https://github.com/RblSb/SyncTube-octosubs) - `ASS`/`SSA` subtitles support
- [qswitcher](https://github.com/aNNiMON/SyncTube-QSwitcher) - raw video quality switcher

### How to use
- Login with any nickname
- Add your video url with "plus" button below (youtube or direct link to mp4 for example)
- Now it plays and syncs for all page users, well done
- You can click "leader" button to get access to global video controls (play/pause, time setting, playback speed)
- If you want to restrict permissions or add admins/emotes, see `Configuration` above

### Intergations
#### Heroku:
- Create app and commit repo to get build
- Remove `user/` folder from `.gitignore` and commit it to change default configuration
- Add `APP_URL` config var with `your-app-link.herokuapp.com` value to prevent sleeping when clients online

### Development
- Install [Haxe 4.3](https://haxe.org/download/), [VSCode](https://code.visualstudio.com) and [Haxe extension](https://marketplace.visualstudio.com/items?itemName=nadako.vshaxe)
- `haxelib install all` to install extern libs
- If you skipped `Setup` section before: `npm ci`
- Open project in VSCode and press `F5` for client+server build and run

### About
- Layout and design by [Austin Riddell](https://github.com/aus-tin)
- [Original idea](https://github.com/calzoneman/sync) by Calvin Montgomery
- Default emotes by [emlan](https://www.deviantart.com/emlan)

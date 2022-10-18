[![Build Status](https://travis-ci.org/Hernior/ngx-youtube-player.svg?branch=master)](https://travis-ci.org/Hernior/ngx-youtube-player)
[![npm version](https://badge.fury.io/js/ngx-youtube-player.svg)](https://badge.fury.io/js/ngx-youtube-player)
[![npm downloads a month](https://img.shields.io/npm/dm/ngx-youtube-player.svg)](https://img.shields.io/npm/dm/ngx-youtube-player.svg)
[![npm downloads a week](https://img.shields.io/npm/dt/ngx-youtube-player.svg)](https://img.shields.io/npm/dt/ngx-youtube-player.svg)

# Angular Youtube Player Component

This is an Angular component based on [youtube player iframe api](https://developers.google.com/youtube/iframe_api_reference).

## Angular Support

**Compatible with Angular v14**, versions follow Angular's version to easily reflect compatibility.
Starting with Angular v14.2.6.

## LICENSE

This fork project is free to use, released under **MIT** license.

## Installation

`npm install @hercilio/ngx-youtube-player`

## Supported API

Currently supported attributes:

### Inputs

- **height** (number) – The width of the video player. The default value is 640.
- **width** (number) – The height of the video player. The default value is 390.
- **videoId** (string) – The YouTube video ID that identifies the video that the player will load.
- **playerVars** (object) – The object's properties identify player parameters that can be used to customize the player.
- **events** (object) – The object's properties identify the events that the API fires and the functions (event listeners) that the API will call when those events occur. In the example, the constructor indicates that the `onPlayerReady` function will execute when the `onReady` event fires and that the `onPlayerStateChange` function will execute when the `onStateChange` event fires.

### outputs

- **ready** (YT.Player) – Implements youtube's player `onReady` event -> sends a the new created yt player instance
- **change** – A state change event channeling the youtube's player instance state event object

## Player object and functions

[YouTube Player API Reference](https://developers.google.com/youtube/iframe_api_reference)
 - videoTitle
 - playerInfo
 - addCueRange()
 - clearVideo()
 - cuePlaylist()
 - cueVideoById()
 - cueVideoByUrl()
 - getApiInterface()
 - getAvailablePlaybackRates()
 - getAvailableQualityLevels()
 - getCurrentTime()
 - getDebugText()
 - getDuration()
 - getMediaReferenceTime()
 - getPlaybackQuality()
 - getPlaybackRate()
 - getPlayerMode()
 - getPlayerState()
 - getPlaylist()
 - getPlaylistId()
 - getPlaylistIndex()
 - getSize()
 - getSphericalProperties()
 - getVideoBytesLoaded()
 - getVideoBytesTotal()
 - getVideoData()
 - getVideoLoadedFraction()
 - getVideoStartBytes()
 - getVideoUrl()
 - getVolume()
 - hideVideoInfo()
 - isMuted()
 - isVideoInfoVisible()
 - loadModule()
 - loadPlaylist()
 - loadVideoById()
 - loadVideoByUrl()
 - logImaAdEvent()
 - mute()
 - nextVideo()
 - pauseVideo()
 - playVideo()
 - playVideoAt()
 - removeCueRange()
 - removeEventListener()
 - seekTo()
 - setLoop()
 - setOption()
 - setPlaybackQuality()
 - setPlaybackRate()
 - setShuffle()
 - setSphericalProperties()
 - setVolume()
 - showVideoInfo()
 - stopVideo()
 - unMute()
 - unloadModule()

## Usage

First, import the YoutubePlayerModule to your module:

```typescript
import { NgxYoutubePlayerModule } from 'ngx-youtube-player';

...

@NgModule({
  ...
  imports: [..., NgxYoutubePlayerModule.forRoot()],
  ...
})
export class AppModule {}
```

Next, use the **youtube-player** component. A Unique Id will be created for this player's instance:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app",
  template: `
    <youtube-player
      width="100%"
      height="400"
      [videoId]="id"
      [playerVars]="{ modestbranding: 1, controls: 1, disablekb: 1, rel: 0, showinfo: 0 }"
      (ready)="playerReady($event)"
      (change)="onVideoChange($event)">
    </youtube-player>
  `,
})
export class AppComponent {
  player: YT.Player;
  private id: string = "L-odCf4MfJc";

  playerReady(player) {
    this.player = player;
    console.log("player instance", player);
  }

  onVideoChange(event) {
    console.log("player state", event.data);
  }
}
```

## Testing

To start developing tdd/bdd style: `npm run dev`
This will: compile ts files, watch for changes and start the test task. Whenever a ts file is changed, it will rerun the tests.

Travis-ci is integrated

## Building & Publish

- npm run build:lib
- cd dist/ngx-youtube-player
- npm publish --access public

# Showcase Examples

- [Soon example...]()
- [Soon example repository...]()
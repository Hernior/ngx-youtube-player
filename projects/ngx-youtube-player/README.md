[![Build Status](https://travis-ci.org/Hernior/ngx-youtube-player.svg?branch=master)](https://travis-ci.org/Hernior/ngx-youtube-player)
[![npm version](https://badge.fury.io/js/ngx-youtube-player.svg)](https://badge.fury.io/js/ngx-youtube-player)
[![npm downloads a month](https://img.shields.io/npm/dm/ngx-youtube-player.svg)](https://img.shields.io/npm/dm/ngx-youtube-player.svg)
[![npm downloads a week](https://img.shields.io/npm/dt/ngx-youtube-player.svg)](https://img.shields.io/npm/dt/ngx-youtube-player.svg)

# Angular Youtube Player Component

This is an Angular component based on [youtube player iframe api](https://developers.google.com/youtube/iframe_api_reference).
This component came out as a result of the [open source project Echoes Player](http://github.com/Hernior/echoes-player) - an alternative player for watching and listening to media from youtube.
Original project: https://github.com/Hernior/ngx-youtube-player

## Angular Support

**Compatible with Angular v14 or later**, versions follow Angular's version to easily reflect compatibility.
Starting with Angular v14.2.5.

## LICENSE

This fork project is free to use, released under **MIT** license.

## Installation

`npm install @hercilio/ngx-youtube-player`

## Supported API

Currently supported attributes:

### Inputs

- **height** (number) - optional height for the player
- **width** (number) - optional width for the player
- **videoId** (string) - will load the specified video by id

### outputs

- **ready** (YT.Player) - implements youtube's player onReady event -> sends a the new created yt player instance
- **change** - a state change event channeling the youtube's player instance state event object

## DEMO

[A Live Demo In StackBlitz](https://stackblitz.com/edit/ngx-youtube-player?file=src%2Fapp%2Fapp.module.ts)

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
      [videoId]="id"
      (ready)="savePlayer($event)"
      (change)="onStateChange($event)"
    ></youtube-player>
  `,
})
export class AppComponent {
  player: YT.Player;
  private id: string = "L-odCf4MfJc";

  savePlayer(player) {
    this.player = player;
    console.log("player instance", player);
  }
  onStateChange(event) {
    console.log("player state", event.data);
  }
}
```

# Showcase Examples

- [Echoes Player](http://orizens.github.io/echoes-player) ([github repo for echoes player](http://github.com/Hernior/echoes-player))

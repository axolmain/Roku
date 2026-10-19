# Moonfin for Roku

A Roku client for Jellyfin and Emby media servers. This glossary fixes the words used for its concepts in code, commits and design discussions.

> **Draft (2026-10-09):** written during an architecture review, from commit history and code. The main developer should confirm or correct these terms.

## Language

### Servers

**Media server**:
A Jellyfin or Emby server the viewer has signed into.
_Avoid_: backend, host

**Server kind**:
Whether a media server is Jellyfin or Emby, which decides its routes, features and quirks.
_Avoid_: server type, flavour

**Signed-in server**:
The media server the viewer's current session belongs to.
_Avoid_: active server, local server, home server

**Item server**:
The media server an item was loaded from. When rows combine several servers, it can differ from the signed-in server.
_Avoid_: remote server (this also means a server reached over the network), owner server

### Libraries

**Library**:
A top-level collection of media on a media server, such as Movies or Shows.
_Avoid_: view (the server's word for it), folder, section

**Hidden library**:
A library the viewer has excluded from My Media on the server. Emby may name it by Guid rather than Id.
_Avoid_: excluded view

**Library order**:
The viewer's chosen order of libraries for one media server, saved to their account.

### Playback

**Direct play**:
The Roku plays the original file as-is.

**Remux**:
The server repackages the file into a container the Roku can play, without re-encoding the video.
_Avoid_: direct stream, server stream

**Transcode**:
The server re-encodes the video.
_Avoid_: re-encode, convert

**Fallback ladder**:
The fixed order of direct play, remux, then transcode that playback moves down when a stream fails or never starts.
_Avoid_: rung, step down, retry chain

**Burn-in**:
Subtitles drawn into the video by the server during a transcode, because the Roku cannot draw them itself.

**Live channel**:
A Live TV channel tuned from the guide. Unlike a recording, it has a live stream the server opens and must close.
_Avoid_: live item (this also covers recordings)

### Details screen

**Details screen**:
The screen for a single item, with its buttons, tracks, metadata and related rows.
_Avoid_: item page, detail page

**Detail layout**:
One of the five ways a details screen can be drawn: Classic, Modern, Nouveau, Minimalist or Spotlight. The viewer picks one in settings.
_Avoid_: style, theme, details style

### Testing

**Environment**:
One combination of a device profile and a server profile that a device test run targets.

**Device profile**:
A Roku device the device tests can sideload to, described by its model and how to reach it.

**Server profile**:
A media server the device tests run against, described by its server kind, version and fixture set.

**Fixture set**:
The fixed media library loaded into a test server, chosen so each scenario has known content.
_Avoid_: test data, seed data

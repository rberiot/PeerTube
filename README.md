<h1 align="center">
  PeerTube
</h1>

<h4 align="center">
Federated (ActivityPub) video streaming platform using P2P (BitTorrent)
directly in the web browser with <a href="https://github.com/feross/webtorrent">WebTorrent</a>.
</h4>

**PeerTube is sponsored by [Framasoft](https://framatube.org/#en), a non-profit
that promotes, spreads and develops free culture in general, and free-libre
software in particular. If you want to support this project, please [consider
donating to them](https://soutenir.framasoft.org/en/).**

<p align="center">
  <strong>Client</strong>

  <br />

  <a href="https://david-dm.org/Chocobozzz/PeerTube?path=client">
    <img src="https://david-dm.org/Chocobozzz/PeerTube.svg?path=client" alt="Dependency Status" />
  </a>

  <a href="https://david-dm.org/Chocobozzz/PeerTube?path=client&type=dev">
    <img src="https://david-dm.org/Chocobozzz/PeerTube/dev-status.svg?path=client" alt="devDependency Status" />
  </a>
</p>

<p align="center">
  <strong>Server</strong>

  <br />

  <a href="https://travis-ci.org/Chocobozzz/PeerTube">
    <img src="https://travis-ci.org/Chocobozzz/PeerTube.svg?branch=develop" alt="Build Status" />
  </a>

  <a href="https://david-dm.org/Chocobozzz/PeerTube">
    <img src="https://david-dm.org/Chocobozzz/PeerTube.svg" alt="Dependencies Status" />
  </a>

  <a href="https://david-dm.org/Chocobozzz/PeerTube?type=dev">
    <img src="https://david-dm.org/Chocobozzz/PeerTube/dev-status.svg" alt="devDependency Status" />
  </a>

  <a href="http://standardjs.com/">
    <img src="https://img.shields.io/badge/code%20style-standard-brightgreen.svg" alt="JavaScript Style Guide" />
  </a>

  <a href="https://kiwiirc.com/client/irc.freenode.net/#peertube">
    <img src="https://img.shields.io/badge/%23peertube-on%20freenode-brightgreen.svg" alt="PeerTube Freenode IRC" />
  </a>
</p>

<br />

<p align="center">
  <a href="https://peertube.cpy.re">
    <img src="https://lutim.cpy.re/mRdBAdeD.png" alt="screenshot" />
  </a>
</p>

## Demonstration

Want to see it in action?

   * Demonstration servers:
     * [peertube.cpy.re](http://peertube.cpy.re)
     * [peertube2.cpy.re](http://peertube2.cpy.re)
     * [peertube3.cpy.re](http://peertube3.cpy.re)
   * [Video](https://peertube.cpy.re/videos/watch/f78a97f8-a142-4ce1-a5bd-154bf9386504)
     to see what the "decentralization feature" looks like

## Why

We can't build a FOSS video streaming alternatives to YouTube, Dailymotion,
Vimeo... with a centralized software. One organization alone may not have
enough money to pay for bandwidth and video storage of its servers.

So we need to have a decentralized network of servers seeding videos (as
[Diaspora](https://github.com/diaspora/diaspora) for example).  But it's not
enough because one video could become famous and overload the server.  It's the
reason why we need to use a P2P protocol to limit the server load.  Thanks to
[WebTorrent](https://github.com/feross/webtorrent), we can make P2P (thus
BitTorrent) inside the web browser, as of today.

## Dependencies

  * nginx
  * PostgreSQL
  * Redis
  * **NodeJS >= 8.x**
  * yarn
  * OpenSSL (cli)
  * **FFmpeg >= 3.x**

## Run using Docker

See the [docker guide](/support/doc/docker.md)

## Production

See the [production guide](/support/doc/production.md).

## Contributing/Test

See the [contributing
guide](/.github/CONTRIBUTING.md)
to see how to test or contribute to PeerTube. Spoiler alert: you don't need to be a
coder to help!

## API REST documentation

For now only on Github:

 * HTML version: [/support/doc/api/html/index.html](/support/doc/api/html/index.html)
 * Swagger/OpenAPI schema: [/support/doc/api/openapi.yaml](/support/doc/api/openapi.yaml)

## Tools

 * [Import videos (YouTube, Dailymotion, Vimeo...)](/support/doc/tools.md)
 * [Upload videos from the CLI](/support/doc/tools.md)

## FAQ

If you have a question, please try to find the answer in the [FAQ](/FAQ.md) first.

## Architecture

See [ARCHITECTURE.md](/ARCHITECTURE.md) for a more detailed explanation.

### Backend

  * The backend is a REST API.
  * Servers communicate with each others with [Activity
    Pub](https://www.w3.org/TR/activitypub/).
  * Each server has its own users who query it (search videos, query where the
    torrent URI of this specific video is...).
  * If a user uploads a video, the server seeds it and sends its followers some
    metadata (name, short description, torrent URI...).
  * A server is a tracker responsible for all the videos uploaded in it.
  * Even if nobody watches a video, it is seeded by the server (through
    [WebSeed protocol](http://www.bittorrent.org/beps/bep_0019.html)) where the
    video was uploaded.

Here are some simple schemes:

<p align="center">

<img src="https://lutim.cpy.re/6Qut3ure.png" alt="Decentralized" />

<img src="https://lutim.cpy.re/NvRAcv6U.png" alt="Watch a video" />

<img src="https://lutim.cpy.re/pqKm3Q5S.png" alt="Watch a P2P video" />

</p>

## License

Copyright (C) 2018 PeerTube Contributors

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

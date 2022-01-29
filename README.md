# level-community

**General discussion, cross-repository efforts and common information for projects in the community.**

> :pushpin: Which module should I use? What is `abstract-level`? Head over to the [FAQ](https://github.com/Level/community#faq).

[![level badge][level-badge]](https://github.com/Level/awesome)
[![Test](https://github.com/Level/community/actions/workflows/test.yml/badge.svg)](https://github.com/Level/community/actions/workflows/test.yml)
[![Donate](https://img.shields.io/badge/donate-orange?logo=open-collective\&logoColor=fff)](https://opencollective.com/level)

## Table of Contents

<details><summary>Click to expand</summary>

- [What is Level?](#what-is-level)
- [FAQ](#faq)
  - [Where do I start?](#where-do-i-start)
  - [What is `abstract-level`?](#what-is-abstract-level)
  - [How do I upgrade to `abstract-level`?](#how-do-i-upgrade-to-abstract-level)
  - [Where can I get support?](#where-can-i-get-support)
  - [Where can I follow progress?](#where-can-i-follow-progress)
- [People](#people)
  - [Collaborators](#collaborators)
  - [Collaborator emeriti](#collaborator-emeriti)
  - [Contributors](#contributors)
- [API](#api)
- [Contributing](#contributing)
- [Donate](#donate)
- [License](#license)

</details>

## What is Level?

**Level is a community and a collection of Node.js modules for creating transparent databases. A solid set of primitives enable powerful databases to be built in userland. They can be embedded or networked, persistent or transient - in short, tailored to your needs.**

At the core of Level are simple key-value stores that follow the characteristics of [LevelDB](https://github.com/google/leveldb). LevelDB is a key-value store built by Google, used in Google Chrome and many other products. It supports arbitrary byte arrays as both keys and values, singular reads and writes, batched writes and bi-directional iterators. LevelDB sorts entries lexicographically by keys which, when combined with ranged iterators, makes for a very powerful query mechanism.

To bring those concepts to Node.js and other JavaScript runtimes, Level utilizes idiomatic Node.js interfaces like [streams](https://nodejs.org/api/stream.html), [events](https://nodejs.org/api/events.html) and [buffers](https://nodejs.org/api/buffer.html). It offers a rich set of data types through [encodings][encoding-down] and allows for extensions like [`subleveldown`][subleveldown] to split a database into evented sections. Underlying stores can be easily swapped to target a wide range of runtime environments. The most common store is [`leveldown`][leveldown] which is a pure C++ binding to LevelDB. [Many alternatives are available](https://github.com/Level/awesome/#stores) such as [`level-js`][level-js] in the browser or [`memdown`][memdown] for an in-memory store.

## FAQ

### Where do I start?

The [`level`][level] module is the recommended way to get started. It offers a persistent database that works in Node.js and browsers. To store data in a different way you might like [`level-mem`][level-mem] for example, which exports the same API as `level` but stores data in-memory. Visit [`Level/awesome`](https://github.com/Level/awesome) to discover more modules.

### What is `abstract-level`?

_If you are new to Level, there is a quick answer: [`abstract-level`][abstract-level] is the new core of Level on top of which several databases are (or will be) implemented. Read on if you're already familiar with Level modules (before 2022) and have used [`level`][level], [`levelup`][levelup], [`abstract-leveldown`][abstract-leveldown], [`encoding-down`][encoding-down] or [`deferred-leveldown`][def-ld]._

Back in 2012, [`levelup`][levelup] offered a Node.js binding for Google's LevelDB. Authored by Rod Vagg, `levelup` exposed the features of LevelDB in a Node.js-friendly way. It had streams, binary support, encodings... all the goodies. Later on, the binding was moved to [`leveldown`][leveldown], so that other stores could be swapped in while retaining the friendly API of `levelup`.

This is when "up" vs "down" naming was born, where databases followed the formula of "level = levelup + leveldown". For example, `level-mem` was a convenience package that bundled `levelup` with `memdown`. The [`abstract-leveldown`][abstract-leveldown] module offered a lower-level abstraction for the "down" part, to encapsulate common logic between "down" stores. Many such stores were written, replacing LevelDB with IndexedDB, RocksDB, in-memory red-black trees, relational databases and more.

Around 2017, further parts were extracted from `levelup` and moved to single-purpose modules. This effectively introduced the concept of "layers", where an implementation of `abstract-leveldown` wasn't necessarily a storage for `levelup` but could also wrap another `abstract-leveldown` implementation. For example, `levelup` encoding logic was extracted to [`encoding-down`][encoding-down]. This changed the database formula to "level = levelup + encoding-down + leveldown". Or in other words: "levelup + layer + layer".

This highly modular architecture led to clean code, where each module had a single responsibility. By this time, the overall API had settled and matured, some contributors moved on to other exciting things and the primary remaining effort was maintenance. This posed new challenges. We worked on test suites, added automated browser tests, code coverage and database manifests.

Yet, releases too often required canary testing in dependents. It was hard to predict the effect of a change. In addition, documentation became fragmented and some modules actually suffered from the high modularity, having to peel off layers to customize behavior. At the same time, we could see that typical usage of a Level database still involved encodings and the other goodies that the original `levelup` had.

Enter [`abstract-level`][abstract-level]. This module merges `levelup`, `encoding-down` and `abstract-leveldown` into a single codebase. Instead of implementing behaviors "vertically" in layers, it is done per database method. Performance-wise `abstract-level` is currently on par with the old modules, or slightly (around 5%) faster than. GC pressure is lower because methods allocate less callback functions. Custom (userland) database methods also benefit from the new architecture, because they can reuse utility methods included in `abstract-level` rather than a layer having to detect and wrap custom methods.

Lastly, `abstract-level` comes with new features, some of which were not possible to implement before. Among them: Uint8Array support, builtin sublevels, atomically committing data to multiple sublevels, and reading multiple or all entries from an iterator in one call.

### How do I upgrade to `abstract-level`?

We've put together several upgrade guides for different modules. For example, if you're currently using `level@7` and no other modules (ignoring transitive dependencies) then it will suffice to read the upgrade guide of `level@8`.

Naming-wise, databases generally use an npm package name in the form of `*-level` while utilities and plugins are called `level-*`. This replaces the [down versus up](https://github.com/Level/abstract-level/issues/6) naming scheme. Similarly, while it was previously helpful for documentation to distinguish between "database" and its "underlying store", now you will mostly just encounter the term "database".

To upgrade, please consult the following table. If you use a combination of the modules listed here, each must be upgraded to its `abstract-level` equivalent.

| Old module                                   | New module                           | Named export <sup>5</sup> | Upgrade guide                               |
| :------------------------------------------- | :----------------------------------- | :------------------------ | :------------------------------------------ |
| [`level`][level] <= 7                        | [`level`][level] >= 8 <sup>1</sup>   | `Level`                   | `level@8`<sup>4</sup> (_not yet available_) |
| [`abstract-leveldown`][abstract-leveldown]   | [`abstract-level`][abstract-level]   | `AbstractLevel`           | [`abstract-level@1`][abstract-level@1]      |
| [`levelup`][levelup]                         | n/a                                  | n/a                       | Depends <sup>3</sup>                        |
| `level` or `levelup` with streams            | [`level-read-stream`][l-read-stream] | `EntryStream`             | [`level-read-stream@1`][l-read-stream@1]    |
| [`leveldown`][leveldown]                     | `classic-level`                      | `ClassicLevel`            | _Not yet available_                         |
| [`level-mem`][level-mem]                     | `memory-level`                       | `MemoryLevel`             | _Not yet available_                         |
| [`memdown`][memdown]                         | `memory-level`                       | `MemoryLevel`             | _Not yet available_                         |
| [`level-js`][level-js]                       | `browser-level`                      | `BrowserLevel`            | _Not yet available_                         |
| [`level-rocksdb`][level-rocksdb]             | `rocks-level`                        | `RocksLevel`              | _Not yet available_                         |
| [`rocksdb`][rocksdb]                         | `rocks-level`                        | `RocksLevel`              | _Not yet available_                         |
| [`multileveldown`][multileveldown]           | `many-level`                         | `ManyLevel`               | _Not yet available_                         |
| [`level-party`][level-party]                 | `rave-level`                         | `RaveLevel`               | _Not yet available_                         |
| [`subleveldown`][subleveldown]<sup>2</sup>   | n/a                                  | n/a                       | [`abstract-level@1`][abstract-level@1]      |
| [`deferred-leveldown`][def-ld]<sup>2</sup>   | n/a                                  | n/a                       | [`abstract-level@1`][abstract-level@1]      |
| [`encoding-down`][encoding-down]<sup>2</sup> | n/a                                  | n/a                       | [`abstract-level@1`][abstract-level@1]      |
| [`level-errors`][level-errors]<sup>2</sup>   | n/a                                  | n/a                       | [`abstract-level@1`][abstract-level@1]      |
| [`level-packager`][level-packager]           | n/a                                  | n/a                       | n/a                                         |
| [`level-supports`][supports] <= 2            | [`level-supports`][supports] >= 3    | `supports`                | n/a                                         |
| [`level-codec`][level-codec] <sup>6</sup>    | [`level-transcoder`][transcoder]     | `Transcoder`              | [`level-transcoder@1`][transcoder@1]        |
| [`level-test`][level-test]                   | n/a                                  | n/a                       | _Not yet available_                         |

<small>

1. Will export `classic-level` in Node and `browser-level` in browsers.
2. Functionality is now included in `abstract-level`.
3. If the module that you're wrapping with `levelup` is listed here then refer to that module's upgrade guide, else see [`abstract-level@1`][abstract-level@1].
4. If browser support is not needed, alternatively use `classic-level` which has the same API.
5. Most new modules use named exports, for example `const { ClassicLevel } = require('classic-level')` instead of `const leveldown = require('leveldown')`.
6. Encodings that follow the `level-codec` interface (without `level-codec` as a dependency) can still be used.

</small>

### Where can I get support?

If you need help - technical, philosophical or other - feel free to [open an issue](https://github.com/Level/community/issues/new/choose) in [`community`](https://github.com/Level/community) or a more specific repository. We don't (yet) use GitHub Discussions, at least until discussions get the ability to [close them](https://github.com/github/feedback/discussions/3097).

You will generally find someone willing to help. Good questions get better and quicker answers. We do not offer paid support. All time is volunteered.

### Where can I follow progress?

Most if not all activity happens on GitHub. See our [project board](https://github.com/orgs/Level/projects/3) to find out what we're working on. Any timelines there are just a rough indication of priority. We cannot guarantee that feature X or Y will actually be released on the given dates.

Subscribe to individual repositories to follow their progress. All releases are accompanied by a changelog and a GitHub Release, which gives you the option to only [subscribe to new releases](https://docs.github.com/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#configuring-your-watch-settings-for-an-individual-repository).

## People

### Collaborators

- [**@finnp**](https://github.com/finnp) - Finn Pauls
- [**@juliangruber**](https://github.com/juliangruber) - Julian Gruber
- [**@mafintosh**](https://github.com/mafintosh) - Mathias Buus
- [**@mcollina**](https://github.com/mcollina) - Matteo Collina
- [**@MeirionHughes**](https://github.com/MeirionHughes) - Meirion Hughes
- [**@peakji**](https://github.com/peakji) - Yichao 'Peak' Ji
- [**@ralphtheninja**](https://github.com/ralphtheninja) - Lars-Magnus Skog
- [**@Raynos**](https://github.com/Raynos) - Jake Verbaten
- [**@rvagg**](https://github.com/rvagg) - Rod Vagg
- [**@vweevers**](https://github.com/vweevers) - Vincent Weevers

### Collaborator emeriti

- [**@brycebaril**](https://github.com/brycebaril) - Bryce Baril
- [**@chesles**](https://github.com/chesles) - j chesley
- [**@chjj**](https://github.com/chjj) - Christopher Jeffrey (JJ)
- [**@cjihrig**](https://github.com/cjihrig) - Colin Ihrig
- [**@deanlandolt**](https://github.com/deanlandolt) - Dean Landolt
- [**@dominictarr**](https://github.com/dominictarr) - Dominic Tarr
- [**@emeryrose**](https://github.com/emeryrose) - Emery Rose Hall
- [**@eugeneware**](https://github.com/eugeneware) - Eugene Ware
- [**@filoozom**](https://github.com/filoozom) - Philippe Schommers
- [**@heapwolf**](https://github.com/heapwolf) - Paolo Fragomeni
- [**@huan**](https://github.com/huan) - Huan (李卓桓)
- [**@jameskyburz**](https://github.com/jameskyburz) - James Kyburz
- [**@jcrugzz**](https://github.com/jcrugzz) - Jarrett Cruger
- [**@kesla**](https://github.com/kesla) - David Björklund
- [**@maxogden**](https://github.com/maxogden) - Max Ogden
- [**@No9**](https://github.com/No9) - Anton Whalley
- [**@nolanlawson**](https://github.com/nolanlawson) - Nolan Lawson
- [**@obastemur**](https://github.com/obastemur) - Oguz Bastemur
- [**@pgte**](https://github.com/pgte) - Pedro Teixeira
- [**@soldair**](https://github.com/soldair) - Ryan Day
- [**@substack**](https://github.com/substack) - James Halliday

### Contributors

- [**@a0viedo**](https://github.com/a0viedo) - Alejandro Oviedo
- [**@abliss**](https://github.com/abliss) - Adam Bliss
- [**@achingbrain**](https://github.com/achingbrain) - Alex Potsides
- [**@adityapurwa**](https://github.com/adityapurwa) - Aditya Purwa
- [**@agentilela**](https://github.com/agentilela) - Alex Gentile
- [**@alessioalex**](https://github.com/alessioalex) - Alexandru Vlăduţu
- [**@andrewrk**](https://github.com/andrewrk) - Andrew Kelley
- [**@ArtskydJ**](https://github.com/ArtskydJ) - Joseph Dykstra
- [**@bewest**](https://github.com/bewest) - Ben West
- [**@bigeasy**](https://github.com/bigeasy) - Alan Gutierrez
- [**@braydonf**](https://github.com/braydonf) - Braydon Fuller
- [**@calvinmetcalf**](https://github.com/calvinmetcalf) - Calvin Metcalf
- [**@chiguireitor**](https://github.com/chiguireitor) - Chiguireitor
- [**@cronopio**](https://github.com/cronopio) - Daniel Aristizabal
- [**@danielravina**](https://github.com/danielravina) - Daniel Ravina
- [**@dcousens**](https://github.com/dcousens) - Daniel Cousens
- [**@deian**](https://github.com/deian) - Deian Stefan
- [**@dey-dey**](https://github.com/dey-dey) - Amadeus J
- [**@diasdavid**](https://github.com/diasdavid) - David Dias
- [**@doowb**](https://github.com/doowb) - Brian Woodward
- [**@emschwartz**](https://github.com/emschwartz) - Evan Schwartz
- [**@fanatid**](https://github.com/fanatid) - Kirill Fomichev
- [**@farskipper**](https://github.com/farskipper) - Matthew Wright
- [**@Gawen**](https://github.com/Gawen) - Gawen Arab
- [**@ggreer**](https://github.com/ggreer) - Geoff Greer
- [**@ghostbar**](https://github.com/ghostbar) - Jose-Luis Rivas
- [**@guybrush**](https://github.com/guybrush) - Patrick
- [**@hansott**](https://github.com/hansott) - Hans Ott
- [**@hden**](https://github.com/hden) - Haokang Den
- [**@heavyk**](https://github.com/heavyk) - kenny
- [**@ivantm**](https://github.com/ivantm) - Ivan Miskovic
- [**@jamesgrayling**](https://github.com/jamesgrayling) - James Grayling
- [**@jfromaniello**](https://github.com/jfromaniello) - José F. Romaniello
- [**@JimLiu**](https://github.com/JimLiu) - Jim Liu
- [**@joyeecheung**](https://github.com/joyeecheung) - Joyee Cheung
- [**@kemitchell**](https://github.com/kemitchell) - Kyle Mitchell
- [**@kessler**](https://github.com/kessler) - Yaniv Kessler
- [**@kumavis**](https://github.com/kumavis) - kumavis
- [**@kytwb**](https://github.com/kytwb) - Amine Mouafik
- [**@l1x**](https://github.com/l1x) - Istvan
- [**@luandro**](https://github.com/luandro) - Luandro
- [**@mateodelnorte**](https://github.com/mateodelnorte) - Matt Walters
- [**@marcooliveira**](https://github.com/marcooliveira) - Marco Oliveira
- [**@mcavage**](https://github.com/mcavage) - Mark Cavage
- [**@mhart**](https://github.com/mhart) - Michael Hart
- [**@michaelnisi**](https://github.com/michaelnisi) - Michael Nisi
- [**@monkeywithacupcake**](https://github.com/monkeywithacupcake) - jess
- [**@montyanderson**](https://github.com/montyanderson) - Monty Anderson
- [**@mscdex**](https://github.com/mscdex) - mscdex
- [**@NickNaso**](https://github.com/NickNaso) - Nicola Del Gobbo
- [**@nrw**](https://github.com/nrw) - Nicholas Westlake
- [**@PascalTemel**](https://github.com/PascalTemel) - Pascal Temel
- [**@pra85**](https://github.com/pra85) - Prayag Verma
- [**@pskupinski**](https://github.com/pskupinski) - Preston Skupinski
- [**@qbit**](https://github.com/qbit) - Aaron Bieber
- [**@qs44**](https://github.com/qs44) - Josh
- [**@raboof**](https://github.com/raboof) - Arnout Engelen
- [**@rasmuserik**](https://github.com/rasmuserik) - RasmusErik Voel Jensen
- [**@refset**](https://github.com/refset) - Jeremy Taylor
- [**@rh0**](https://github.com/rh0) - Ryan Oles
- [**@RichardLitt**](https://github.com/RichardLitt) - Richard Littauer
- [**@ryanramage**](https://github.com/ryanramage) - Ryan Ramage
- [**@sorribas**](https://github.com/sorribas) - Eduardo Sorribas
- [**@sandfox**](https://github.com/sandfox) - James Butler
- [**@sandersn**](https://github.com/sandersn) - Nathan Shively-Sanders
- [**@seriousManual**](https://github.com/seriousManual) - Manuel Ernst
- [**@shama**](https://github.com/shama) - Kyle Robinson Young
- [**@sharvil**](https://github.com/sharvil) - Sharvil Nanavati
- [**@staltz**](https://github.com/staltz) - André Staltz
- [**@Tapppi**](https://github.com/Tapppi) - Tapani Moilanen
- [**@TehShrike**](https://github.com/TehShrike) - Josh Duff
- [**@thebergamo**](https://github.com/thebergamo) - Marcos Vinicius Bérgamo
- [**@thefoxis**](https://github.com/thefoxis) - Karolina Szczur
- [**@thlorenz**](https://github.com/thlorenz) - Thorsten Lorenz
- [**@timkuijsten**](https://github.com/timkuijsten) - Tim Kuijsten
- [**@timoxley**](https://github.com/timoxley) - Tim Oxley
- [**@vjrantal**](https://github.com/vjrantal) - Ville Rantala
- [**@watson**](https://github.com/watson) - Thomas Watson
- [**@wbolster**](https://github.com/wbolster) - wouter bolsterlee
- [**@willwhite**](https://github.com/willwhite) - Will White
- [**@wolfeidau**](https://github.com/wolfeidau) - Mark Wolfe
- [**@yoshuawuyts**](https://github.com/yoshuawuyts) - Yoshua Wuyts
- [**@zixia**](https://github.com/zixia) - Huan LI

_Is your name missing? Send us a pull request!_

## API

This repository also used to hold a small amount of metadata on past and present contributors. They can be accessed from code by:

```js
console.log(require('level-community'))
```

This metadata is no longer maintained and the npm package will be deprecated at some point. Contributors are instead documented in this README under [People](#people).

## Contributing

[`Level/community`](https://github.com/Level/community) is an **OPEN Open Source Project**. This means that:

> Individuals making significant and valuable contributions are given commit-access to the project to contribute as they see fit. This project is more like an open wiki than a standard guarded open source project.

See the [Contribution Guide](https://github.com/Level/community/blob/master/CONTRIBUTING.md) for more details.

## Donate

Support us with a monthly donation on [Open Collective](https://opencollective.com/level) and help us continue our work.

## License

[MIT](LICENSE)

[level-badge]: https://leveljs.org/img/badge.svg

[abstract-level]: https://github.com/Level/abstract-level

[abstract-level@1]: https://github.com/Level/abstract-level/blob/main/UPGRADING.md#100

[abstract-leveldown]: https://github.com/Level/abstract-leveldown

[def-ld]: https://github.com/Level/deferred-leveldown

[encoding-down]: https://github.com/Level/encoding-down

[level]: https://github.com/Level/level

[level-codec]: https://github.com/Level/codec

[level-errors]: https://github.com/Level/errors

[level-js]: https://github.com/Level/level-js

[level-mem]: https://github.com/Level/mem

[level-packager]: https://github.com/Level/packager

[level-party]: https://github.com/Level/party

[l-read-stream]: https://github.com/Level/read-stream

[l-read-stream@1]: https://github.com/Level/read-stream/blob/main/UPGRADING.md#100

[level-rocksdb]: https://github.com/Level/level-rocksdb

[supports]: https://github.com/Level/supports

[level-test]: https://github.com/Level/level-test

[transcoder]: https://github.com/Level/transcoder

[transcoder@1]: https://github.com/Level/transcoder/blob/main/UPGRADING.md#100

[leveldown]: https://github.com/Level/leveldown

[levelup]: https://github.com/Level/levelup

[memdown]: https://github.com/Level/memdown

[multileveldown]: https://github.com/Level/multileveldown

[rocksdb]: https://github.com/Level/rocksdb

[subleveldown]: https://github.com/Level/subleveldown

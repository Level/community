# level-community

**General discussion, cross-repository efforts and common information for projects in the community.**

[![level badge][level-badge]](https://github.com/Level/awesome)
[![Test](https://github.com/Level/community/actions/workflows/test.yml/badge.svg)](https://github.com/Level/community/actions/workflows/test.yml)
[![Donate](https://img.shields.io/badge/donate-orange?logo=open-collective&logoColor=fff)](https://opencollective.com/level)

## What is Level?

**Level is a community and a collection of Node.js modules for creating transparent databases. A solid set of primitives enable powerful databases to be built in userland. They can be embedded or networked, persistent or transient - in short, tailored to your needs.**

At the core of Level are simple key-value stores that follow the characteristics of [LevelDB](https://github.com/google/leveldb). LevelDB is a key-value store built by Google, used in Google Chrome and many other products. It supports arbitrary byte arrays as both keys and values, singular reads and writes, batched writes and bi-directional iterators. LevelDB sorts entries lexicographically by keys which, when combined with ranged iterators, makes for a very powerful query mechanism.

To bring those concepts to Node.js and other JavaScript runtimes, Level utilizes idiomatic Node.js interfaces like [streams](https://nodejs.org/api/stream.html), [events](https://nodejs.org/api/events.html) and [buffers](https://nodejs.org/api/buffer.html). It offers a rich set of data types through [encodings](https://github.com/Level/encoding-down) and allows for extensions like [`subleveldown`](https://github.com/Level/subleveldown) to split a database into evented sections. Underlying stores can be easily swapped to target a wide range of runtime environments. The most common store is [`leveldown`](https://github.com/Level/leveldown) which is a pure C++ binding to LevelDB. [Many alternatives are available](https://github.com/Level/awesome/#stores) such as [`level-js`](https://github.com/Level/level-js) in the browser or [`memdown`](https://github.com/Level/memdown) for an in-memory store.

The [`level`](https://github.com/Level/level) module is the recommended way to get started. Visit [`awesome`](https://github.com/Level/awesome) to discover more modules. See our [project board](https://github.com/orgs/Level/projects/2) to find out what we're working on. If you need help - technical, philosophical or other - feel free to open an issue in [`community`](https://github.com/Level/community) or a more specific repository.

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

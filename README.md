# level-community

> General discussion, cross-repo efforts and common information for projects in the community.

[![level badge][level-badge]](https://github.com/Level/awesome)
[![Backers on Open Collective](https://opencollective.com/level/backers/badge.svg?color=orange)](#backers)
[![Sponsors on Open Collective](https://opencollective.com/level/sponsors/badge.svg?color=orange)](#sponsors)

## What is Level?

**Level is a community and a collection of Node.js modules for creating transparent, isomorphic databases. A solid set of primitives enable powerful databases to be built in userland. They can be embedded or networked, persistent or transient, in short, tailored to your needs.**

At the core of Level are simple key-value stores that follow the characteristics of [LevelDB](https://github.com/google/leveldb). LevelDB is a key-value store built by Google, used in Google Chrome and many other products. It supports arbitrary byte arrays as both keys and values, singular reads and writes, batched writes and bi-directional iterators. LevelDB sorts entries lexicographically by keys which, when combined with ranged iterators, makes for a very powerful query mechanism.

To bring those concepts to Node.js and other JavaScript runtimes, Level utilizes idiomatic Node.js interfaces like [streams](https://nodejs.org/api/stream.html), [events](https://nodejs.org/api/events.html) and [buffers](https://nodejs.org/api/buffer.html). It offers a rich set of data types through [encodings](https://github.com/Level/encoding-down) and allows for extensions like [`subleveldown`](https://github.com/Level/subleveldown) to split a database into evented sections. Underlying stores can be easily swapped to target a wide range of runtime environments. The most common store is [`leveldown`](https://github.com/Level/leveldown) which is a pure C++ binding to LevelDB. [Many alternatives are available](https://github.com/Level/awesome/#stores) such as [`level-js`](https://github.com/Level/level-js) in the browser or [`memdown`](https://github.com/Level/memdown) for an in-memory store.

The [`level`](https://github.com/Level/level) module is the recommended way to get started. Visit [`awesome`](https://github.com/Level/awesome) to discover more modules. If you need help - technical, philosophical or other - feel free to open an issue in [`community`](https://github.com/Level/community) or a more specific repository.

## API

This repository also holds a small amount of metadata on past and present contributors. They can be accessed from code by:

```js
var contributors = require('level-community').contributors
console.log(contributors)
```

We use this metadata across the board to render [`CONTRIBUTORS.md`](CONTRIBUTORS.md) files based on git history. If you have contributed to one or more Level repositories in the past but don't see social metadata next to your name, add yourself to [`contributors.json`](contributors.json) and send us a PR.

## Contributing

[`Level/community`](https://github.com/Level/community) is an **OPEN Open Source Project**. This means that:

> Individuals making significant and valuable contributions are given commit-access to the project to contribute as they see fit. This project is more like an open wiki than a standard guarded open source project.

See the [Contribution Guide](https://github.com/Level/community/blob/master/CONTRIBUTING.md) for more details.

## Donate

To sustain [`Level`](https://github.com/Level) and its activities, become a backer or sponsor on [Open Collective](https://opencollective.com/level). Your logo or avatar will be displayed on our 28+ [GitHub repositories](https://github.com/Level), [npm](https://www.npmjs.com/) packages and (soon) [our website](http://leveldb.org). 💖

### Backers

[![Open Collective backers](https://opencollective.com/level/backers.svg?width=890)](https://opencollective.com/level)

### Sponsors

[![Open Collective sponsors](https://opencollective.com/level/sponsors.svg?width=890)](https://opencollective.com/level)

## License

[MIT](LICENSE.md) © 2012-present [Contributors](CONTRIBUTORS.md).

[level-badge]: http://leveldb.org/img/badge.svg

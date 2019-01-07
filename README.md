# level-community

> A place for general discussion, cross-repo efforts and common information related to projects in the `Level` community.

[![level badge][level-badge]](https://github.com/Level/awesome)
[![Backers on Open Collective](https://opencollective.com/level/backers/badge.svg?color=orange)](#backers)
[![Sponsors on Open Collective](https://opencollective.com/level/sponsors/badge.svg?color=orange)](#sponsors)

## What is Level?

**Level is a Node.js library and community for creating embedded databases - think SQLite, but non relational!**

It was first and foremost inspired by [LevelDB](https://github.com/google/leveldb), a simple key-value store built by Google. It's used in Google Chrome and many other products. LevelDB supports arbitrary byte arrays as both keys and values, singular get, put and delete operations, batched put and delete, bi-directional iterators and simple compression using the very fast [Snappy](http://google.github.io/snappy/) algorithm.

The way you iterate over a LevelDB makes it very usable for a myriad of use cases! LevelDB stores entries sorted lexicographically by keys, which makes the [streaming interface](https://opencollective.com/level#createReadStream) of `levelup` that exposes LevelDB iterators as [Readable Streams](https://nodejs.org/docs/latest/api/stream.html#stream_readable_streams) a very powerful query mechanism.

It's flexible in another major respect, that is that the underlying storage backends are swappable! The most common store is [leveldown](https://github.com/level/leveldown/) which provides a pure C++ binding to LevelDB. [Many alternative stores are available](https://github.com/Level/awesome/#stores) such as [level.js](https://github.com/level/level.js) in the browser or [memdown](https://github.com/level/memdown) for an in-memory store. They typically support strings and Buffers for both keys and values. For a richer set of data types you can wrap the store with [encoding-down](https://github.com/level/encoding-down).

## API

Contributors can be accessed from code by:

```js
var contributors = require('level-community').contributors
console.log(JSON.stringify(contributors, null, 2))
```

When creating a new project. Either link to this repository or include it as a dependency in `package.json`.

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

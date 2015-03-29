# level-community

<img alt="LevelDB Logo" height="100" src="http://leveldb.org/img/logo.svg">

**Meta data on members of the LevelDB community**

## Usage

Exposes a simple `json` object with level maintainers meta data. The keys correspond to user names on github. Useful for mapping between github user space to npm user space etc.

```js
var community = require('level-community')
console.log(JSON.stringify(community, null, 2))
```

```json
{
  "rvagg": {
    "name": "Rod Vagg",
    "email": "r@va.gg",
    "npm": "rvagg",
    "twitter": "rvagg",
    "homepage": "http://r.va.gg"
  },
  "juliangruber": {
    "name": "Julian Gruber",
    "email": "julian@juliangruber.com",
    "npm": "juliangruber",
    "twitter": "juliangruber",
    "homepage": "http://juliangruber.com"
  },
  ...
}
```

## License &amp; copyright

Copyright (c) 2012-2015 LevelUP contributors.

LevelUP is licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included LICENSE.md file for more details.

LevelUP is licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included LICENSE.md file for more details.

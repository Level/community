# level-community

<img alt="LevelDB Logo" height="100" src="http://leveldb.org/img/logo.svg">

**Gathers common information related to projects in the `Level` community**

When creating a new project. Either link to this repository or include it as a dependency in `package.json`.

### License &amp; Copyright

Copyright (c) 2012-2015 `Level` contributors.

`Level` projects are licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included [`LICENSE.md`](https://github.com/level/community/blob/master/LICENSE.md) file for more details.

### Contributing

`Level` projects are **OPEN Open Source Projects**. This means that:

> Individuals making significant and valuable contributions are given commit-access to a project to contribute as they see fit. A project is more like an open wiki than a standard guarded open source project.

See the [`CONTRIBUTING.md`](https://github.com/level/community/blob/master/CONTRIBUTING.md) file for more details.

### Contributors

`Level` projects are only possible due to the excellent work of the following contributors:

<table><tbody>
<tr><th align="left">Rod Vagg</th><td><a href="https://github.com/rvagg">GitHub/rvagg</a></td><td><a href="http://twitter.com/rvagg">Twitter/@rvagg</a></td></tr>
<tr><th align="left">John Chesley</th><td><a href="https://github.com/chesles/">GitHub/chesles</a></td><td><a href="http://twitter.com/chesles">Twitter/@chesles</a></td></tr>
<tr><th align="left">Jake Verbaten</th><td><a href="https://github.com/raynos">GitHub/raynos</a></td><td><a href="http://twitter.com/raynos">Twitter/@raynos</a></td></tr>
<tr><th align="left">Dominic Tarr</th><td><a href="https://github.com/dominictarr">GitHub/dominictarr</a></td><td><a href="http://twitter.com/dominictarr">Twitter/@dominictarr</a></td></tr>
<tr><th align="left">Max Ogden</th><td><a href="https://github.com/maxogden">GitHub/maxogden</a></td><td><a href="http://twitter.com/maxogden">Twitter/@maxogden</a></td></tr>
<tr><th align="left">Lars-Magnus Skog</th><td><a href="https://github.com/ralphtheninja">GitHub/ralphtheninja</a></td><td><a href="http://twitter.com/ralphtheninja">Twitter/@ralphtheninja</a></td></tr>
<tr><th align="left">David Björklund</th><td><a href="https://github.com/kesla">GitHub/kesla</a></td><td><a href="http://twitter.com/david_bjorklund">Twitter/@david_bjorklund</a></td></tr>
<tr><th align="left">Julian Gruber</th><td><a href="https://github.com/juliangruber">GitHub/juliangruber</a></td><td><a href="http://twitter.com/juliangruber">Twitter/@juliangruber</a></td></tr>
<tr><th align="left">Paolo Fragomeni</th><td><a href="https://github.com/hij1nx">GitHub/hij1nx</a></td><td><a href="http://twitter.com/hij1nx">Twitter/@hij1nx</a></td></tr>
<tr><th align="left">Anton Whalley</th><td><a href="https://github.com/No9">GitHub/No9</a></td><td><a href="https://twitter.com/antonwhalley">Twitter/@antonwhalley</a></td></tr>
<tr><th align="left">Matteo Collina</th><td><a href="https://github.com/mcollina">GitHub/mcollina</a></td><td><a href="https://twitter.com/matteocollina">Twitter/@matteocollina</a></td></tr>
<tr><th align="left">Pedro Teixeira</th><td><a href="https://github.com/pgte">GitHub/pgte</a></td><td><a href="https://twitter.com/pgte">Twitter/@pgte</a></td></tr>
<tr><th align="left">James Halliday</th><td><a href="https://github.com/substack">GitHub/substack</a></td><td><a href="https://twitter.com/substack">Twitter/@substack</a></td></tr>
<tr><th align="left">Jarrett Cruger</th><td><a href="https://github.com/jcrugzz">GitHub/jcrugzz</a></td><td><a href="https://twitter.com/jcrugzz">Twitter/@jcrugzz</a></td></tr>
<tr><th align="left">Mathias Buus</th><td><a href="https://github.com/mafintosh">GitHub/mafintosh</a></td><td><a href="https://twitter.com/mafintosh">Twitter/@mafintosh</a></td></tr>
<tr><th align="left">Oguz Bastemur</th><td><a href="https://github.com/obastemur">GitHub/obastemur</a></td><td><a href="https://twitter.com/obastemur">Twitter/@obastemur</a></td></tr>
<tr><th align="left">Huan LI</th><td><a href="https://github.com/zixia">GitHub/zixia</a></td><td><a href="https://twitter.com/zixia">Twitter/@zixia</a></td></tr>
</tbody></table>

### Api

Contributors can be accessed from code by:

```js
var contributors = require('level-community').contributors
console.log(JSON.stringify(contributors, null, 2))
```

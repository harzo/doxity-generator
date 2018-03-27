# Doxity Generator

### Documentation Generator for Solidity Contracts
##### Powered by [Gatsby](https://github.com/gatsbyjs/gatsby)
This is the fork of working [Doxity-Simpleton](https://github.com/RyanHendricks/doxity-simpleton)
project created in order to clear Ryan's solution and instructions.

## Getting Started

```
git clone https://github.com/harzo/doxity-generator.git
```

### Edit the following files to match your Github Repo to use Github Pages

- .doxityrc - no changes needed if you plan to use master branch /docs folder for github pages
- /doxity/config.toml - "linkPrefix = "/yours-repo-url"" must match your Github Repo
- package.json - the following fields must match your Github Repo to use Github Pages
```
"author": "YOUR NAME",
"main": "docs/index.html",
"repository": {
    "type": "git",
    "url": "git+https://github.com/username/yours-repo-url.git"
  },
"homepage": "git+https://github.com/username/yours-repo-url/",
```

## Add Contracts

Copy your solidity contracts to the `contracts` folder.

##### *Important!*
Doxity won't generate docs for multiple contracts in one file.\
Especially for docs limitations you should consider place each contract
in new file.

Also optional imports from `node_modules` are not visible for doxity.
If your project contains, for example, imports like this:
```
import { Ownable } from "zeppelin-solidity/contracts/ownership/Ownable.sol";
import { SafeMath } from "zeppelin-solidity/contracts/math/SafeMath.sol";
```

you should copy whole `zeppelin-solidity` to `contracts` folder and change
paths to `./zeppelin-solidity/...`

## Build the docs

```bash
# install doxity dependencies
$ cd doxity-simpleton/doxity
$ yarn

# return to root dir
$ cd ..

# install project dependencies from root folder
$ yarn

# build the docs
$ doxity build
```

## Github Pages

You can choose your `master` branch to store docs. To do so simply put generated
docs in `docs/` folder.

Second option is pushing docs to orphan branch named `gh-pages`, created like this
```git
git checkout --orphan <branch_name>
```

In the settings of your repository choose Github Pages source.
It should be rebuilded after each commit.

---
For a more in depth look at how this works and for additional commands please see: [Original Readme](https://github.com/DigixGlobal/doxity/blob/master/README.md)

[Demo Site](https://hitchcott.github.io/doxity-demo/docs/MetaCoin/)

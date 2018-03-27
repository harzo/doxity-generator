# Doxity Docs Generator

### Documentation Generator for Solidity Contracts
##### Powered by [Gatsby](https://github.com/gatsbyjs/gatsby)
This is the fork of working [Doxity-Simpleton](https://github.com/RyanHendricks/doxity-simpleton)
project created in order to clear Ryan's solution and instructions.

## Getting Started

```
git clone https://github.com/harzo/doxity-generator.git
```

## Docs generation

It is recommended by me to keep this project separately from the project
we want to document.\
The main reason for that is a fact that Doxity won't
generate docs for multiple contracts in one file.

Because of this limitations you are forced to place each contract in a
separate file but this approach may ruin yours project structure.

Also optional imports from `node_modules/` are not visible for Doxity.
If your project contains, for example, imports like this:
```
import { Ownable } from "zeppelin-solidity/contracts/ownership/Ownable.sol";
import { SafeMath } from "zeppelin-solidity/contracts/math/SafeMath.sol";
```
you need to copy whole `zeppelin-solidity` to `contracts` folder and change
paths to `./zeppelin-solidity/...`

##### Steps

1. Copy your solidity contracts to the `contracts` folder.
2. Refactor contracts files to single contract in one file.
3. Copy solidity contracts imports to the `contracts` folder and change related paths
4. Copy `README.md` to root folder
5. Make sure the following files are complete and match your Github Repo:
    - `doxity/config.toml`:
        ```
        linkPrefix = "/yours-repo-url"
        ```
    - `package.json`:
        ```
        "name": "yours-project-name",
        "author": "Your Name",
        "description": "Yours Project description",
        "main": "docs/index.html",
        "repository": {
            "type": "git",
            "url": "git+https://github.com/username/yours-repo-url.git"
          },
        "homepage": "git+https://github.com/username/yours-repo-url/"
        ```

## Build the docs

1. Install Doxity dependencies
    ```
    $ cd doxity
    $ yarn
    $ cd ..
    ```
2. Install project dependencies from root folder
    ```
    $ yarn
    ```
3. Build the docs
    ```
    $ npm run docs
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
For a more in depth look at how this works and for additional commands please see:

[Original Readme](https://github.com/DigixGlobal/doxity/blob/master/README.md)

[Demo Site](https://hitchcott.github.io/doxity-demo/docs/MetaCoin/)

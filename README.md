# yarn-bug

A potential bug with handling package extensions was introduced in [this commit](https://github.com/yarnpkg/berry/commit/871bd7517919c2209e78e78a3ce8b9c66a70f939).
We had set up packageExtensions to fix some issues in dependency trees related to the deck.gl package to ensure there is only one version of the package loaded.
I created a simplified version of the dependency tree and package extensions in this project. The linked changes cause some of the packageExtensions to not be applied,
which then creates duplicate versions of deck.gl in the tree. 

How to reproduce duplicates

```sh
yarn set version berry && yarn
```

See changes to yarn.lock and .yarn/cache

To test fix for duplicates

```sh
yarn set version from sources --repository git@github.com:ganemone/berry.git --branch extensions && yarn
```

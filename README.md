Building with Parcel fails when importing a `.less` file from a `.tsx` file, with browserslist configured to
support Android UC (or QQ browser). The default browserslist setting as of June 2024 has support for those
browsers.

## How to reproduce

1. Clone this repository
2. `yarn install`
3. `yarn parcel build index.html --no-cache`

You'll see an error like this:

```
🚨 Build failed.

Error: Expected content key f9dfd8f407ec5b22 to exist

  Error: Expected content key f9dfd8f407ec5b22 to exist
      at nullthrows (/Users/mroloux/dev/parcel-less-import-react/node_modules/nullthrows/nullthrows.js:7:15)
      at AssetGraph.getNodeIdByContentKey (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/graph/lib/ContentGraph.js:67:38)
      at /Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/SymbolPropagation.js:52:82
      at Array.map (<anonymous>)
      at propagateSymbols (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/SymbolPropagation.js:52:61)
      at AssetGraphBuilder.build (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/requests/AssetGraphRequest.js:174:62)
      at async Object.run (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/requests/AssetGraphRequest.js:62:37)
      at async RequestTracker.runRequest (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/RequestTracker.js:673:20)
      at async Object.run (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/requests/BundleGraphRequest.js:106:11)
      at async RequestTracker.runRequest (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/RequestTracker.js:673:20)

Error: Does not have node 45
    at AssetGraph._assertHasNodeId (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/graph/lib/Graph.js:449:13)
    at AssetGraph.getNodeIdsConnectedFrom (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/graph/lib/Graph.js:81:10)
    at visitChildren (/Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/requests/AssetGraphRequest.js:148:47)
    at /Users/mroloux/dev/parcel-less-import-react/node_modules/@parcel/core/lib/requests/AssetGraphRequest.js:144:67
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

If you remove the `browserslist` entry from `package.json` and build again, the build succeeds.

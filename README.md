
`main` will be where the electron file is.

these must be added: `main, author, description`

`author` will show as the "publisher" when installed in an OS

the following need to be added to the package.json.
```
"main": "public/main.js",
"author": "Juan",
"description": "test_app",
"scripts": {...}, <- collapsed
"build": {
    "extends": null,
    "appId": "com.example.electron-cra",
    "files": [
      "dist/**/*",
      "build/**/*",
      "node_modules/**/*",
      "package.json"
    ],
    "directories": {
      "buildResources": "assets"
    }
  },
```

npm installs

```
@electron/remote
```

npm -D installs:

```
concurrently
cross-env
electron
electron-builder
wait-on
```

add theses to the script
The `electron:build` will point to the built app not the `public` folder

```
"electron:serve": "concurrently -k \"cross-env BROWSER=none npm run start\" \"npm run electron:start\"",
"electron:build": "npm run build && electron-builder -c.extraMetadata.main=build/main.js",
"electron:start": "wait-on tcp:3000 && electron ."
```

`npm run electron:serve` will run the app, it uses `electron:start` but it will stop the app from running in the browser


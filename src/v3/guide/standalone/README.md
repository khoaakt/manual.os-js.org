---
description: A guide on how to run OS.js in standalone mode
full_title: Standalone Mode
---

# Standalone Mode Guide

You can run OS.js in standalone mode, whic does not require the backend to work.

This has some limitations described below.

Edit your `src/client/config.js` file and add the following setting:

> [info] Remember to rebuild with `npm run build` after you modify the configuration.

```javscript
{
  standalone: true
}
```

## With a webserver

In this mode, it will run just like normal except the default provided authentication, storage and filesystems.

You can drop the `dist/` contents into any directory that is hosted by any web server.

Services and providers that does not interact with the OS.js backend will work as expected.

## Without webserver

You can launch OS.js from `file://` (i.e. just opening the html file in `dist/`) by modifying the client configuration.

Note that HTTP requests cannot be made in this mode, so any feature that requires a network or internet connection will be unavailable.

Since requests cannot be made you have to add the package manifest to your configuration.

Edit your `src/client/config.js` file and add the following setting:

```javscript
{
  packages: {
    metadata: require('../../dist/metadata.json')
  }
}
```

> [info] You must run the `npm run package:discover` command before building and rebuild the client if you run any subsequent package discovery.


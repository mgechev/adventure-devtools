# Angular DevTools Adventure Experience

This repository contains the implementation of the Angular DevTools immersive experience for Google I/O Adventure 2021.

## How to start?

```
git clone git@github.com:mgechev/adventure-devtools
cd adventure-devtools
npx serve .
```

## Integration points

The demo runs an Angular application on the page and has an iframe that starts Angular DevTools. Angular DevTools communicates via message passing with the Angular application. The **iframe running Angular DevTools must have the id `devtools`**. This is how the application establishes the communication channel with the tooling.

### Bootstrapping the app

To bootstrap the Angular application (which will presumably run within Adventure) you need to:

1. Include the application script (`<script src="app.js"></script>`)
1. Add an element to the page called `<app></app>` that matches the bootstrap component. I've used `display: none` on this element because it doesn't have to be visible to the user
1. (Optional) Stylesheet to apply styles to the iframe (`app-styles.css`)
1. An iframe that references Angular DevTools (`<iframe id="devtools" src="devtools.html"></iframe>`, the `id` must equal `devtools`)

### Bootstrapping Angular DevTools

To start Angular DevTools, you'd need an HTML file that references:

1. The bundle which contains Angular DevTools `devtools.js`
1. Angular DevTools' styles (`devtools-styles.css`)
1. Material fonts `https://fonts.googleapis.com/icon?family=Material+Icons`
1. An element that will match the bootstrap component of Angular DevTools called `<app-root></app-root>`

### How to solve the quest?

When you see Angular DevTools at the bottom of the page, select the `fixme` component. After that update its `state` property from `broken` to `fixed`. This action will call the global `window.__ngAppFixed__` function. Within that function you could propagate the action to Adventure. Currently, there's a dummy demo which just alerts a message. You can find it in `index.html`.

**Please let me know how the integration goes! I'd love to assist if there's anything I can help with!**

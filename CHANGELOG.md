# Changelog

## Version 3.0.0

- Add `data-app-region` to be able to drag a div to move the window.
- `executeJavascript` changed a bit: if the result of the executed code is a promise the callback result will be the resolved value of the promise. We recommend that you use the returned Promise to handle code that results in a Promise.

  ```js
  contents
    .executeJavaScript(
      'fetch("https://jsonplaceholder.typicode.com/users/1").then(resp => resp.json())',
      true
    )
    .then(result => {
      console.log(result) // Will be the JSON object from the fetch call
    })
  ```

- Fix bounds methods to handle inverted y as well as the initial y position of the window.

## Version 2.1.7

- Fix remotely executing javascript on a webview.

## Version 2.1.6

- Fix events dispatching to the wrong event emitter.

## Version 2.1.5

- Fix a bug in the 'will-navigate' event.

## Version 2.1.4

- Fix a bug preventing events to be triggered (introduced in v2.1.3).

## Version 2.1.3

- Make sure that `webContents.executeJavascript` is executed after the webview is loaded.
- Wrap event handlers in try/catch to log the error (and avoid crashing Sketch).

## Version 2.1.2

- Fix a crash when loading an https resource.

## Version 2.1.1

- Enable developer tools by setting `options.webPreferences.devTools` to true.

## Version 2.1.0

- Add support for showing the webview as a modal (aka sheet) by setting `options.modal` to `true`.

## Version 2.0.1

- Fix the loading of css/js assets from a local web page

## Version 2.0.0

:warning: This version requires Sketch >= 51.

- The webview is now backed by `WKWebview`.
- Instead of importing `sketch-module-web-view/client`, you now communicate with the plugin using `window.postMessage`.

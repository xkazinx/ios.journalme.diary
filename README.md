# Journal Me, the diary entry editor (2017)

The web pages that an iOS diary app, Journal Me, loaded inside its web view to show and edit an entry: a rich-text editor with a toolbar, sized for the phone, that the app drives from native code. HTML, CSS and jQuery over the `bootstrap-wysiwyg` plugin; no backend, the app keeps the entries. Written in 2017, kept as it was.

## What it does

- `index.html` is the **reading view**: the entry's HTML in a white sheet, "Press on Edit Journal to input content" until the app loads one.
- `entry.html` is the **editor**: a toolbar with font family and size, bold / italic / underline / strikethrough, bullet and numbered lists, indent and outdent, the four alignments, links, a picture from the device's library (an invisible file input over the picture button), undo and redo, and voice dictation where WebKit offers it. The text itself is a `contenteditable` div.
- Both pages measure the screen (or the viewport on a phone) and resize the sheet to it, so the editor fills the web view with no page scroll.
- Hooks for the app: `SetEditable(true|false)` switches the sheet between reading and writing, `IsEditable()` reports it, the placeholder clears on the first tap, and pictures dropped into the entry are scaled to the sheet's width every half second.

## What it shows

- The browser's `execCommand` editing model driven through a small plugin, with a toolbar declared in HTML (`data-edit="bold"`, `fontSize 5`, `insertImage`...), and the plugin's hotkeys.
- A web page designed as a component of a native app: fixed to the viewport, no navigation, a few global functions as its API.

## Running it

Open `entry.html` in a browser, or `index.html` for the reading view; everything is static. In the app the same files were served from the bundle.

## Layout

```
index.html           the reading view
entry.html           the editor and its toolbar
script.js            mobile detection and the window measurement shared by both pages
index.css            the sheet's style
bootstrap-wysiwyg.js the editor plugin;  external/  jquery.hotkeys and google-code-prettify;  fontawesome/, font-awesome/  the icons
```

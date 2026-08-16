# X Media Grid Restore

A minimal Chrome extension and userscript that ask X to use its legacy profile
media layout. They run only on `https://x.com/*`, send no network requests, and
store no data. The Chrome extension requests no optional permissions; its only
site access is `https://x.com/*`.

## How it works

Before X initializes its React application, the extension changes these two
feature flags in both the default and per-user configurations:

- `responsive_web_profile_redesign_enabled`
- `rweb_media_carousel_enabled`

Both values are changed from `true` to `false`. This works only while X still
ships the legacy media-grid component.

## Install in Chrome

1. Open `chrome://extensions`.
2. Enable **Developer mode**.
3. Click **Load unpacked**.
4. Select this `x-media-grid-restore` folder.
5. Reload an X profile's media page.

## Install with Tampermonkey

1. Open `x-media-grid-restore.user.js` from the repository's Raw view.
2. Let Tampermonkey install the userscript.
3. Reload an X profile's media page.

The script must run at the real `document-start` in the page's main JavaScript
world. In Tampermonkey on Chrome Manifest V3, set **Content Script API** to
**UserScripts API Dynamic** if the grid does not appear. Chrome may also require
**Allow User Scripts** in Tampermonkey's extension settings or Developer mode.

## Remove

Open `chrome://extensions` and remove **X Media Grid Restore**. Reload X to
return to its standard layout.

## Verification

Open a profile's media page and confirm that media items appear in a compact
gallery instead of full tweet cards. If the page remains a timeline, X has
either changed the relevant flags or removed the legacy component.

## Known limitation

X no longer maintains the legacy media timeline reliably. On some profiles,
the restored grid can stop requesting older media after a few dozen items.

## License

Released under the [MIT License](LICENSE).

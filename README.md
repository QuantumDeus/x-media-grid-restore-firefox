# X Media Grid Restore

A minimal local FireFox extension that asks X to use its legacy profile media
layout. It runs only on `https://x.com/*`, has no background process, requests
no Chrome permissions, sends no network requests, and stores no data.

<img width="1536" height="986" alt="image" src="https://github.com/user-attachments/assets/b04c23ff-aad7-49e2-9cbe-c64b28162bf5" />


## How it works

Before X initializes its React application, the extension changes these two
feature flags in both the default and per-user configurations:

- `responsive_web_profile_redesign_enabled`
- `rweb_media_carousel_enabled`

Both values are changed from `true` to `false`. This works only while X still
ships the legacy media-grid component.



## Install in Firefox

1. Download the signed `.xpi` file.
2. Open Firefox and go to `about:addons`.
3. Click the gear icon.
4. Select **Install Add-on From File**.
5. Choose the downloaded `.xpi` file and click **Add**.
6. Reload an X profile’s media page.

## Remove

Open `about:addons`, find **X Media Grid Restore**, click the three-dot menu, and select **Remove**. Reload X to return to its standard layout.
## Verification

Open a profile's media page and confirm that media items appear in a compact
gallery instead of full tweet cards. If the page remains a timeline, X has
either changed the relevant flags or removed the legacy component.

## License

Released under the [MIT License](LICENSE).

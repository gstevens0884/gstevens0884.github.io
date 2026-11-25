# Square Fit (PWA)

A static site: no build step, no dependencies. Put the folder on any HTTPS host and it becomes installable.

## Files
- `index.html`            the whole app
- `manifest.webmanifest`  name, colors and icons for installing
- `sw.js`                 service worker: offline support
- `icons/`                app icons (192, 512, maskable 512, Apple touch icon, favicon)

## Try it on your computer
    cd square-fit-pwa
    python3 -m http.server 8000
Open http://localhost:8000 in Chrome or Edge. Localhost counts as secure, so the install icon appears in the address bar.
Opening index.html straight from the file system will not work: service workers need http(s).

## Put it online (all free, all HTTPS)
- Netlify: drag the folder onto app.netlify.com/drop
- Cloudflare Pages: create a project and upload the folder
- GitHub Pages: push the folder to a repo and enable Pages
Serve it from the top of a site or from its own folder. Everything uses relative paths, so a sub-folder works too.

## Installing
- Chrome, Edge (computer or Android): the "Install app" button in the page header, or the install icon in the address bar.
- iPhone and iPad: open it in Safari, tap Share, then "Add to Home Screen".
- Safari on Mac: File menu, "Add to Dock".

## How saving works
- Computer: files download normally.
- Phone and tablet: saving a single image opens the share sheet, so you can pick Save to Photos or send it straight to Instagram. ZIP files download instead.

## Offline
The app opens offline after the first visit. The fonts and the HEIC converter are saved the first time they are used online, so HEIC files from a non-Safari browser need one online use before they work offline.

## Updating
Upload the new files. Installed copies refresh in the background and show the new version the next time the app is opened after that.
If you rename or add files, also change `CACHE` at the top of `sw.js` (for example to `square-fit-v2`) and add the new files to `SHELL`.

## Notes
- Your photos never leave the device. Presets and settings are saved in the browser's local storage on that device.
- Browsers can clear local storage for sites you have not opened in a long while. Installed apps are generally kept.


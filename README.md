# Focus - Timer website

Public support and privacy pages for the macOS app. Plain HTML and CSS; no build step or dependencies.

- Home: https://ebisbe.github.io/focus-timer-site/
- Support: https://ebisbe.github.io/focus-timer-site/support/
- Privacy: https://ebisbe.github.io/focus-timer-site/privacy/
- Contact: focustimer.support@proton.me

## Publish once

In this repository on GitHub, open **Settings → Pages**. Choose **Deploy from a branch**, select **main** and **/ (root)**, and save. After the deployment completes, check both public pages before using their URLs in App Store Connect. Subsequent pushes to `main` publish automatically.

## Edit and preview

Edit `index.html`, `support/index.html`, `privacy/index.html`, or `styles.css` directly. From this directory, run:

```sh
python3 -m http.server 8000
```

Visit http://localhost:8000/. Relative links work both locally and under the GitHub Pages project path. Keep the privacy policy consistent with the shipping app, and update its effective date when the policy changes.

## Maintain from the app repository

The app repository includes this repository as its `website/` Git submodule. Clone the app with `git clone --recurse-submodules`, or initialize an existing checkout with `git submodule update --init website`.

To change the website from the app checkout:

```sh
git -C website switch main
# Edit the website files, then review and commit the intended changes.
git -C website add index.html support/index.html privacy/index.html styles.css
git -C website commit -m "Update website content"
git -C website push origin main
git add website
git commit -m "Update website submodule"
```

The website commit must be pushed before sharing the updated app submodule reference. To pull website updates into the app, use `git submodule update --remote website`, review the changes, and commit the updated reference.

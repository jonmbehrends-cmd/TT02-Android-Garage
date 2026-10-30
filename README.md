# TT-02 Android Garage

A mobile-first, offline-capable Tamiya TT-02 inventory and build-cost progressive web app.

## Install on Android

Enable GitHub Pages using **Settings → Pages → Deploy from branch → main → /(root) → Save**. Once the Pages deployment finishes, visit https://jonmbehrends-cmd.github.io/TT02-Android-Garage/ in Chrome on your Android phone, then **⋮ → Add to Home screen / Install app**.

## Price checks

Starter prices in the inventory are **illustrative estimates**, not verified live offers. The **Prices** tab can fetch current Google Shopping listings through a separately deployed Cloudflare Worker in `worker.js`. To activate:

1. Create a Cloudflare account and a SerpApi account and obtain a SerpApi API key.
2. Install Wrangler (`npm install -g wrangler`) and authenticate (`wrangler login`).
3. In this repository run `wrangler secret put SERPAPI_KEY`, pasting the SerpApi key into the secure prompt.
4. Run `wrangler deploy` and copy the HTTPS `*.workers.dev` URL.
5. In the app's **Prices** tab, enter that Worker URL. Tap **Check prices** to retrieve listings.

Never commit the SerpApi key to GitHub. Price checking is on-demand; it does not currently run unattended or send alerts. Search results may include mismatched products; verify seller, item and shipping before purchase.

## Privacy and data

Inventory is stored in the current browser's localStorage. Use **Settings → Export JSON** to back up parts; import is available in the same tab. Offline operation works after the service worker successfully caches the app. Private API secrets stay only on your Cloudflare Worker; no secret is included in this public repository.

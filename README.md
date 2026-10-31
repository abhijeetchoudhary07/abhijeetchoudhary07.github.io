# abhijeetchoudhary07.github.io

The root GitHub Pages site for `abhijeetchoudhary07`, served at
<https://abhijeetchoudhary07.github.io/>.

It exists because Google Play and Android both look for association files at
the **root** of a developer's website. A project page such as
`/PDF-APP/` cannot serve them — only a repository named exactly
`abhijeetchoudhary07.github.io` can.

## What is here

| Path | Why |
| ---- | --- |
| `.well-known/assetlinks.json` | Digital Asset Links. Lets Android open `https://abhijeetchoudhary07.github.io/arrow-escape/p?...` share links directly in Arrow Escape instead of the browser. |
| `.nojekyll` | **Required.** GitHub Pages runs Jekyll by default, and Jekyll silently drops files and folders beginning with a dot — including `.well-known/`. Without this file `assetlinks.json` returns 404. |
| `index.html` | A plain landing page, so the domain root is not a 404. |

## assetlinks.json

The fingerprint is the **Play App Signing** certificate for
`com.arrowescape.linepuzzle`, copied from
Play Console → Protected with Play → App signing → Digital Asset Links JSON.

It is the key Google signs the distributed APKs with, not a local keystore, so
it stays correct no matter which machine builds the bundle.

To add another app, append a second object to the array — do not replace the
existing one.

Verify after any change:

```
https://developers.google.com/digital-asset-links/tools/generator
```

## app-ads.txt is deliberately NOT here yet

`app-ads.txt` belongs at the root of this site, but it is missing on purpose.

The copy in the Arrow Escape repo still carries `pub-3940256099942544`, which
is **Google's public test publisher ID**, not ours. Publishing an
`app-ads.txt` is an authoritative statement: advertisers treat any seller not
listed in it as unauthorised. Serving a file that names Google's demo account
and omits the real publisher is therefore worse than serving no file at all —
it can suppress legitimate ad demand.

Add it only once AdMob → Settings → Account information gives the real
`pub-…` ID:

```
google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
```

Then set this site as the developer website in Play Console → Store listing,
and AdMob will crawl it within about 24 hours.

# rs-wiki-redirector

A lightweight browser extension that redirects old RuneScape Fandom wiki pages to their equivalents on [runescape.wiki](https://runescape.wiki).

For example:

```
https://runescape.fandom.com/wiki/Vorago  →  https://runescape.wiki/w/Vorago
```

The page name, along with any query string or anchor is preserved.

## How it works

The extension uses Chrome's [declarativeNetRequest](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest) API to rewrite matching top-level navigations before they load. No page content is read, no network requests are logged, and nothing runs on pages outside of `runescape.fandom.com`.

- [`manifest.json`](manifest.json) — declares the extension, its `declarativeNetRequest` permission, and the ruleset.
- [`rules.json`](rules.json) — a single regex rule matching `runescape.fandom.com/wiki/<Page>` and redirecting to `runescape.wiki/w/<Page>`.

Only top-level page navigations (`main_frame`) are redirected, so API calls and embedded resources are left untouched.

## Privacy

The extension requests permission only for `runescape.fandom.com`. It performs redirects entirely on-device via static rules and collects no data.

## License

MIT

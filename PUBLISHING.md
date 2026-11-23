# Publishing an app to the McOS Store

1. Build and test your app in McOS (`python mcos.py build` and `python mcos.py install`).
2. Run `python mcos.py publish`. It checks the package (`mcos.py check`), and writes:
   - `apps/<id>/<id>-<version>.mca`
   - the entry for `index.json`
   - any screenshots listed in `screens=` into `apps/<id>/screens/`
3. Fork this repository, copy those files in, add your entry to `index.json`, and open a **pull request** called `Add <App name> <version>` (or `Update ...`).
4. A maintainer checks it and merges it. Within about an hour every server running the mod picks it up.

## Rules

- Your own work only, or code whose licence lets you share it. Say which licence in `license`.
- No commercial game data (DOOM WADs other than shareware/Freedoom, ROMs, ...).
- Nothing harmful: no programs that wipe other people's files, hide what they do, or spam notifications.
- An update keeps the same `id` and has a higher `version`.

## index.json entry

```json
{
  "id": "hello.mauvecore",
  "name": "Hello",
  "version": "1.0.0",
  "publisher": "MauveCore",
  "category": "Utilities",
  "type": "window",
  "about": "One line about the app.",
  "license": "MIT",
  "file": "apps/hello.mauvecore/hello.mauvecore-1.0.0.mca",
  "size": 12345,
  "sha256": "...",
  "screens": [],
  "added": "2026-11-23",
  "updated": "2026-11-23"
}
```

`id`: 3-47 characters, `a-z 0-9 . -`, and the same as the `id=` in your app.txt. `size` and `sha256` are the package's; the server refuses a download that doesn't match.

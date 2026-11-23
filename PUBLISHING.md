# Publishing an app to the McOS Store

1. Build and test your app in McOS (`python mcos.py build` and `python mcos.py install`).
2. **Fork** this repository on GitHub and clone your fork.
3. Run `python mcos.py publish MyApp --store PATH-TO-YOUR-FORK`. It checks the package and:
   - puts it in `apps/<id>/<id>-<version>.mca` (an older version of yours is removed)
   - copies the screenshots listed in `screens=` into `apps/<id>/screens/`
   - adds your entry to `index.json`, or updates it (size + sha256 filled in)
4. Commit, push, and open a **pull request** called `Add <App name> <version>` (or `Update ...`).
5. A maintainer checks it and merges it. Within about an hour every server running the mod picks it up.

No git? Run `publish` without `--store`: it makes `MyApp/build/publish/` with the files and `entry.json`. Upload the
`apps/<id>` folder to your fork on github.com, paste `entry.json` into the `apps` list in `index.json`, and open the
pull request there.

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
  "updated": "2026-11-23",
  "whatsnew": "Optional: what changed in this version."
}
```

Servers check every package against `size` and `sha256` and skip entries with a bad id, version or path.

`id`: 3-47 characters, `a-z 0-9 . -`, and the same as the `id=` in your app.txt. `size` and `sha256` are the package's; the server refuses a download that doesn't match.

# McOS Store

The online app catalogue for **McOS**, the operating system that runs on the computers in the MCPC Minecraft mod.

Every Minecraft server running the mod downloads `index.json` and the packages in `apps/` from here, keeps copies in its world folder, and shows them in the **McOS Store** app on every computer on that server. If the server is offline, the Store shows the copies it already has.

## What's in here

| Path | What |
|---|---|
| `index.json` | The app list the Store reads (one entry per app) |
| `apps/<id>/<id>-<version>.mca` | The app packages (zip files made by the McOS SDK) |
| `apps/<id>/screens/` | Optional screenshots (.bmp) |
| `PUBLISHING.md` | How to get your app into the Store |

## Making an app

Get `McOS-SDK.zip`, install LLVM (clang + ld.lld) and Python 3, then:

```
python mcos.py new MyApp        # --cpp for C++, --terminal for a terminal program
cd MyApp
python mcos.py build
python mcos.py install          # try it in McOS through the shared folder
```

When it works, see [PUBLISHING.md](PUBLISHING.md).

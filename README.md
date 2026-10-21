# KI CLASH

Arena fighter prototype that runs in the browser, built on Three.js r128.

## Play

The 3D stages are loaded from `stages/`, which browsers block when the page is opened straight from disk. Serve the folder over http instead:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

GitHub Pages works too. Opened as a plain file, only the Wasteland stage is available.

## Model viewer and roster editor

`viewer.html` works as a single file: open it straight from disk and it pulls the models from this GitHub repo (it needs an internet connection). When served with the repo, it reads `models/` instead.

The left panel is the roster. Each box is one character select icon. Each row inside it is a skin, and the chips are that skin's forms in order, with the first one as the base form. The star marks the default skin, and its base form is the icon's portrait. Drag chips to:

- reorder or move forms between skins,
- make a new skin (the "new skin" zone, or drop the chip on a character icon at the bottom),
- give a model its own icon (the "new character" zone),
- take it off the roster (Unassigned).

Double-click a name to rename it. The roster is saved in the browser. EXPORT downloads it as `kiclash-roster.json` and COPY JSON copies it, so it can go into the game.

To add a model, put the `.glb` in `models/` and add a line to `MODELS` at the top of the script in `viewer.html`.

## Stages

Pick a stage on the character select screen:

| Stage | File |
| --- | --- |
| Wasteland | built in code |
| West City | `stages/west_city.glb` |
| Island | `stages/island.glb` |

The stage models were compressed with [glTF-Transform](https://gltf-transform.dev/) (`optimize --compress meshopt --texture-compress webp`) to keep them under GitHub's file size limits. `lib/` holds the matching Three.js r128 `GLTFLoader` and meshopt decoder.

To add a stage, compress the `.glb` the same way, drop it in `stages/`, and add an entry to `STAGES` in `index.html`. Use `scale`, `x`, `y` and `z` to put the stage's fighting floor at height 0 near the centre.

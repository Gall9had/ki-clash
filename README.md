# KI CLASH

Arena fighter prototype that runs in the browser, built on Three.js r128.

## Play

The 3D stages are loaded from `stages/`, which browsers block when the page is opened straight from disk. Serve the folder over http instead:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

GitHub Pages works too. Opened as a plain file, only the Wasteland stage is available.

## Stages

Pick a stage on the character select screen:

| Stage | File |
| --- | --- |
| Wasteland | built in code |
| West City | `stages/west_city.glb` |
| Island | `stages/island.glb` |

The stage models were compressed with [glTF-Transform](https://gltf-transform.dev/) (`optimize --compress meshopt --texture-compress webp`) to keep them under GitHub's file size limits. `lib/` holds the matching Three.js r128 `GLTFLoader` and meshopt decoder.

To add a stage, compress the `.glb` the same way, drop it in `stages/`, and add an entry to `STAGES` in `index.html`. Use `scale`, `x`, `y` and `z` to put the stage's fighting floor at height 0 near the centre.

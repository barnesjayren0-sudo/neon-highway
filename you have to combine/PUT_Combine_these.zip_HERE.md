# Input folder — you have to combine

## For the repo owner

Upload **`Combine_these.zip`** into this folder (`you have to combine/`).

GitHub’s web UI: **Add file → Upload files** → drop `Combine_these.zip` here → Commit.

Or from a terminal:

```bash
cd neon-highway
mkdir -p "you have to combine"
cp /path/to/Combine_these.zip "you have to combine/"
git add "you have to combine/Combine_these.zip"
git commit -m "Add Combine_these.zip input archive"
git push origin main
```

## For GLM 5.3 Flash

1. Extract `Combine_these.zip` from this folder.
2. Combine all extracted Godot/project pieces into **one Mobile Godot 4** project.
3. When finished, output a **`.zip`** into the **`Result/`** folder at the repo root.

Do not skip the Result zip step.

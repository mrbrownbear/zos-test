# Zo's Pasta interactive experience

A six chapter Three.js landing page built from the supplied Zo's Pasta logo and seven generated food GLBs. Scroll changes the camera and product state. Flavour controls swap the modeled bowls, and the five addon controls move ingredients into the chosen bowl. The final action opens the supplied Facebook page.

## Run

From this folder, serve the files with a static HTTP server, such as `python3 -m http.server 8080`, then open `http://localhost:8080`. A file URL will not load ES modules and GLBs correctly.

No account, API key, or build step is required. The Three.js runtime and model files are included. The optional Google font request falls back to local system fonts when unavailable.

## Assets and performance

The seven generated GLBs are full quality masters and total about 190 MB. The mac bowl loads first and releases the preloader. The other models load afterward; the Enter button and a 12 second timeout keep navigation available if a model stalls. For public hosting, optimize geometry and textures and serve the models from a durable CDN with correct caching. This package uses a unique path for every model.

## Verification

Source syntax was checked with `node --check main.js`. The 3D source models were inspected as GLBs. Browser access to localhost was blocked in the current workspace, so visual and interaction testing in a browser remains the publication gate.


## 3D loader fix

The seven original full-resolution GLB models are unchanged. The broken local Three.js bundle was replaced at runtime by a pinned Three.js 0.180.0 import map. Models now load directly from `public/models/` with visible byte progress and the remaining large GLBs load sequentially to avoid a simultaneous memory/network spike. Serve this folder over HTTP, for example `python -m http.server 8080`, then open `http://localhost:8080`.

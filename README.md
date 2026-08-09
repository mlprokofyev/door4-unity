# door4-unity

Door 4 of [Doors](https://github.com/mlprokofyev/doors-web) — **Perun**, a hybrid 2D/3D isometric adventure built with Unity 6 (WebGL).

This repo carries the **pre-built** Unity WebGL production output (Unity builds cannot run in plain CI — they require the Unity editor and a license). The `npm run build` step just copies the committed files into `dist/`, matching the contract expected by [doors-deploy-orchestrator](https://github.com/mlprokofyev/doors-deploy-orchestrator).

## Contents

```
index.html      Unity WebGL bootstrap page (all asset URLs relative — works under /doors/4/)
Build/          Unity WebGL production build (.unityweb, decompression fallback — no special server headers needed)
```

## Updating the build

1. In the Unity project, run the menu item **Perun → Build WebGL (Production)**
   (non-development: debug tools are compiled out, debug components stripped from scenes, `Debug.Log` silenced).
2. Copy `Build/WebGL-Prod/index.html` and `Build/WebGL-Prod/Build/` into this repo
   (keep the `#back-to-hub` link in `index.html`).
3. Commit and push — then trigger the orchestrator:
   ```
   gh workflow run deploy.yml -R mlprokofyev/doors-deploy-orchestrator
   ```

## Local preview

```
npm run build && npx serve dist
```

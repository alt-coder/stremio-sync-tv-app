# Stremio Sync — TizenBrew application module

Packages the patched Stremio shell locally through TizenBrew. The app loads even
if the VM is down; only the waveform/auto-sync API needs the VM.

## Install

1. TizenBrew → **Modules** → **Add module** → **GitHub**.
2. Enter:

   ```
   alt-coder/stremio-sync-tv-app
   ```

3. Launch **Stremio Sync (local shell)**.

## Config

`app/index.html` contains:

```html
window.__STREMIO_SYNC_SERVER__ = "http://109.123.248.61:7011";
window.__DISABLE_SERVICE_WORKER__ = true;
```

If the VM is on the LAN, change that URL to the LAN IP and repush, then purge
jsDelivr:

```
https://purge.jsdelivr.net/gh/alt-coder/stremio-sync-tv-app/app/index.html
```

## Scope

- App shell: TizenBrew/jsDelivr, so it opens without the VM.
- Streams: remote addons, independent of the VM.
- Waveform/auto-sync: `http://<vm>:7011/api/...`, so the VM must be reachable.
- Without the VM, use **Sync by ear** in the editor.

# IPSW URL Installer — GitHub Pages + Codespaces

A small static web app for GitHub Pages. Paste a direct IPSW URL and click **Download IPSW**.

## GitHub Pages

1. Upload this folder to a GitHub repository.
2. Open **Settings → Pages**.
3. Select **Deploy from a branch**, choose your branch, and select `/ (root)`.
4. Open the published Pages URL.

## GitHub Codespaces

Open the repository in Codespaces. The included `.devcontainer/devcontainer.json` provides a lightweight static-server environment. You can also preview `index.html` with any local static server.

## Limitations

This is a browser download helper, not an iPhone firmware flashing utility. GitHub Pages cannot directly install firmware on an iPhone. A remote IPSW host may also block browser requests with CORS or other download restrictions; in that case, opening the direct URL in the browser may be necessary.

No Apple firmware is bundled in this project.

# 星脈 · GitHub Pages

Use this directory's contents as a dedicated repository root, including hidden files. The complete website is in `docs/`; no Node build, backend, Sites configuration or original image-source directory is required.

## Publish

In the repository's Pages settings, choose branch publishing and select the branch containing these files with `/docs` as its folder. [GitHub instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

Alternatively, choose GitHub Actions as the Pages source and manually run **Publish GitHub Pages**. Its workflow uploads only `docs/` and has no automatic push trigger. [Workflow setup](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

Runtime asset URLs are relative, so the viewer also works at a repository subpath. `.nojekyll` preserves the prebuilt site. Search and social-preview metadata use the canonical public URL configured in `lib/seo.mjs`; if the repository or domain changes, update that file in the source project and rebuild before publishing. Keep the URL's trailing slash so preview images resolve inside the project path.

## Files

- `docs/index.html`: online viewer with the packed sprite sheet.
- `docs/og.png`: original social-preview card, shared by Open Graph and X metadata.
- `docs/星脈.html`: self-contained offline viewer.
- `docs/星脈.html.gz`: compressed offline copy; decompress before opening directly.
- `docs/compression.json`: hashes and sizes of the normal files and gzip sidecars.
- `publish-manifest.json`: complete package inventory.

The online viewer references normal filenames. Gzip sidecars are retained, but no GitHub Pages response-header behavior is assumed; the local preview's gzip middleware is not deployed.

Preparation does not upload or publish anything. Review the game's asset publication permissions and the site's visibility before publishing.

To regenerate this directory, run `npm run build:pages` in the original `star-viewer` source project. Packaging refuses to overwrite custom files or modified generated files.

# Thoth Plugins

Community plugins and themes for [Thoth](https://github.com/anitnilay20/thoth).

## Themes

| Plugin | Description | Variants |
|---|---|---|
| [One Dark Pro](one-dark-pro/) | One Dark Pro colour scheme | One Dark Pro |

## File readers

Thoth reads JSON, NDJSON, CSV, Parquet and DuckDB databases out of the box.
These plugins add the formats whose reader DuckDB keeps as a separate download.

| Plugin | Opens | Extension | Download |
|---|---|---|---|
| [Excel Reader](duckdb-excel/) | `.xlsx`, `.xlsm` | `excel` (core) | 7.5 MB |
| [SQLite Reader](duckdb-sqlite/) | `.sqlite`, `.db` | `sqlite` (core) | 26 MB |
| [Arrow Reader](duckdb-arrow/) | `.arrow`, `.arrows`, `.ipc` | `arrow` (community) | 2 MB |

A reader plugin ships **no binary**. It is a few kilobytes declaring which
DuckDB extension to ask for; DuckDB already hosts a build per platform and per
its own version and picks the right one. Carrying the `.duckdb_extension` files
here would mean owning that whole matrix by hand and re-uploading it on every
DuckDB release.

Install one from **Marketplace → File readers** inside Thoth, or accept the
offer Thoth shows above a file that needs it.

## Installing a Plugin

Copy the plugin directory to your Thoth plugins folder and restart Thoth:

```bash
#macos
cp -r <plugin-dir> ~/Library/Application Support/thoth

# Linux
cp -r <plugin-dir> ~/.config/thoth/plugins/

# Windows
xcopy <plugin-dir> %APPDATA%\thoth\plugins\<plugin-dir> /E
```

Then enable it under **Settings → Plugins**.

## Releasing a Plugin

Each plugin has its own GitHub Actions workflow in [.github/workflows/](.github/workflows/). Trigger a release by pushing a tag in the form `<plugin-id>-v<version>`:

```bash
git tag one-dark-pro-v1.0.0
git push origin one-dark-pro-v1.0.0

# The readers share one workflow, keyed off the tag:
git tag duckdb-excel-v1.0.0
git push origin duckdb-excel-v1.0.0
```

The entry must already exist in `manifest.toml` — the workflow rewrites
`download_url`, `sha256` and `version` in place and fails loudly if it finds no
section to rewrite, rather than releasing something nothing points at.

The workflow zips the plugin directory, creates a GitHub Release with the zip as a downloadable artifact, and updates `manifest.toml` with the new `download_url` and `sha256`. Releases can also be triggered manually via *Actions → Run workflow*.

## Contributing

See [PLUGIN_SYSTEM.md](https://github.com/anitnilay20/thoth/blob/main/docs/PLUGIN_SYSTEM.md) for the full plugin authoring guide.

# Thoth Plugins

Community plugins and themes for [Thoth](https://github.com/anitnilay20/thoth).

## Themes

| Plugin | Description | Variants |
|---|---|---|
| [One Dark Pro](one-dark-pro/) | One Dark Pro colour scheme | One Dark Pro |

## Installing a Plugin

Copy the plugin directory to your Thoth plugins folder and restart Thoth:

```bash
# macOS / Linux
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
```

The workflow zips the plugin directory, creates a GitHub Release with the zip as a downloadable artifact, and updates `manifest.toml` with the new `download_url` and `sha256`. Releases can also be triggered manually via *Actions → Run workflow*.

## Contributing

See [PLUGIN_SYSTEM.md](https://github.com/anitnilay20/thoth/blob/main/docs/PLUGIN_SYSTEM.md) for the full plugin authoring guide.

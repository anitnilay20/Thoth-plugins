# One Dark Pro

One Dark Pro colour scheme for [Thoth](https://github.com/anitnilay20/thoth).

## Variants

| Variant | Mode |
|---|---|
| One Dark Pro | Dark |

## Colors

| Token | Value | Usage |
|---|---|---|
| `bg` | `#282c34` | Main editor background |
| `bg_panel` | `#21252b` | Sidebar / panel background |
| `bg_sunken` | `#1e2127` | Title bar / deepest background |
| `surface` | `#2c313a` | Input fields, table row alt |
| `surface_raised` | `#3e4451` | Hover state |
| `surface_active` | `#4b5263` | Active / selected state |
| `fg` | `#abb2bf` | Primary text |
| `fg_muted` | `#5c6370` | Comments, placeholders |
| `accent` | `#61afef` | Primary accent (blue) |
| `accent_secondary` | `#c678dd` | Secondary accent (purple) |
| `syntax_key` | `#e06c75` | JSON / code keys |
| `syntax_string` | `#98c379` | String values |
| `syntax_number` | `#d19a66` | Number values |
| `syntax_bool` | `#56b6c2` | Boolean values |
| `syntax_punctuation` | `#abb2bf` | Brackets, colons |
| `success` | `#98c379` | Success indicators |
| `warning` | `#e5c07b` | Warning indicators |
| `error` | `#e06c75` | Error indicators |
| `info` | `#56b6c2` | Info indicators |
| `indent_guide` | `#3b4048` | Indent guide lines |

## Installation

Download `one-dark-pro.zip` from the [latest release](../../releases/latest), then extract and copy the folder to your Thoth plugins directory:

```bash
# macOS
unzip one-dark-pro.zip -d ~/Library/Application Support/thoth/one-dark-pro

# Linux
unzip one-dark-pro.zip -d ~/.config/thoth/plugins/one-dark-pro

# Windows
Expand-Archive one-dark-pro.zip -DestinationPath "$env:APPDATA\thoth\plugins\one-dark-pro"
```

Restart Thoth and select the theme under **Settings → Appearance → Theme**.

## Releasing

Releases are published automatically by the [GitHub Actions workflow](../.github/workflows/release-one-dark-pro.yml). Two ways to trigger it:

**Tag push (recommended)**
```bash
git tag one-dark-pro-v1.0.0
git push origin one-dark-pro-v1.0.0
```

**Manual dispatch** — go to *Actions → Release · one-dark-pro → Run workflow* and enter the version number.

The workflow packages `plugin.toml`, `theme.json`, and `README.md` into `one-dark-pro.zip`, creates a GitHub Release with the zip as a downloadable artifact, and updates `manifest.toml` with the new `download_url` and `sha256`.

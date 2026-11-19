# npm Packages addon for Rian

An independent, single-file addon for [Rian](https://github.com/FatalMistake02/rian). No npm installation or companion script is needed. All npm-specific URLs, field mappings, and filtering rules live in `npm.json`; Rian supplies generic JSON metadata support.

## Install

1. Download [npm.json](https://raw.githubusercontent.com/FatalMistake02/rian_npm/main/npm.json).
2. In Rian, open **Settings → addons → + Add addon** and select the downloaded file. Save settings.
3. Open **npm Packages** in the overview, press **Enter** to focus its rows, and select a package. **N** or **Enter** opens its npm page. **Ctrl+R** refreshes the data.

In project details, the shortcut is **N Open npm**. Lowercase **n** still opens Notes.

Requires a Rian build with generic addon `metadata` support. Older releases reject that field. Until this support ships in a release, build Rian from its current source. Existing installations can reimport this manifest to upgrade while retaining their settings.

## Display and filtering

The addon reads each saved project's root `package.json`, including scoped package names. It displays the local version, npm's published `latest` version, license, and deprecation notice. Version differences do not imply that either version is newer.

**Only show published packages** is enabled by default under **Settings → addons → npm Packages**. Private projects, custom registries, missing names, unpublished packages, and failed lookups are hidden. Candidates remain hidden during the first lookup. Turn the setting off to show private, unpublished, and other named package candidates too.

Rows follow Rian's project order: favorites first, then most recently used, then project name. Workspace packages must be saved individually as Rian projects.

Detection confirms a matching package name on npm; it cannot prove ownership. If an ordinary app uses another publisher's package name, hide this addon for that project in Rian's project settings.

## Requests and updates

Checks run in the background while Rian is open, with up to four checks at once, an eight-second timeout, a 1 MiB response limit, and a five-minute cache. Private packages and custom registries are never sent to the public npm registry. No project scripts or npm commands run.

Rian stores a copy of imported manifests. To apply an edited manifest, increase its addon version and reimport it. This addon also provides a raw manifest update URL for Rian's addon update checks.

## License

MIT. See [LICENSE](LICENSE).

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.2.0-beta.1] - 2026-11-11

First beta of 0.2.0. Please report anything that behaves differently from 0.1.2.

### Added

- Support for **Minecraft 1.26.60** with LeviLamina 26.60.x, which is now the version BeetrootSkin is installed as by default. Minecraft 1.26.51 with LeviLamina 26.51.x is still supported and gets its own build of every release, so nothing is lost by updating.
  - BeetrootSkin is compiled against one LeviLamina line at a time, so each release now ships one download per line: `beetrootskin-client-win-x64-ll26.60.zip` and `beetrootskin-client-win-x64-ll26.51.zip`, and the API SDK as `beetrootskin-sdk-client-win-x64-ll26.60.zip` and `beetrootskin-sdk-client-win-x64-ll26.51.zip`.

### Changed

- The package is now described by `lip.toml` of format 4 instead of `tooth.json`, so installing it needs a LeviLauncher that reads it. The command-line [lip](https://github.com/LiteLDev/lip) 0.40.0 and later manages server installations only and cannot install this client-only mod. Older releases stay installable with older lip.
- Each supported LeviLamina line is a variant named after it: `26_60` for 26.60.x and `26_51` for 26.51.x. The default variant, and `client` — the variant earlier releases were installed as — are the newest line, so LeviLauncher keeps updating existing installs and simply moves you to 26.60.
  - To stay on Minecraft 1.26.51, pick the `26_51` variant (`github.com/MiracleForest/BeetrootSkin#26_51`) on the mod's page in LeviLauncher.
  - Your settings in `mods/BeetrootSkin/config/` are kept either way.
- The downloads are now lip mod archives: the files sit at the root of the ZIP instead of inside a `BeetrootSkin/` folder. Extract one into `mods/BeetrootSkin/`, not into `mods/`.

## [0.1.2] - 2026-11-01

### Changed

- The repository moved to [MiracleForest/BeetrootSkin](https://github.com/MiracleForest/BeetrootSkin); links point there now.
- The lip package is now `github.com/MiracleForest/BeetrootSkin`: install with `lip install github.com/MiracleForest/BeetrootSkin#client`. To move an existing install over: with lip 0.36.0 or later, `lip update` moves it to the new path automatically; with older lip, run `lip uninstall github.com/LiteLDev/BeetrootSkin#client` and then `lip install github.com/MiracleForest/BeetrootSkin#client`. Either way `mods/BeetrootSkin/config/` is kept. Versions 0.1.1 and older still name the old path, `github.com/LiteLDev/BeetrootSkin`, and install from it (by the new path they need lip 0.35.0 or later).

## [0.1.1] - 2026-10-24

### Added

- A logo, and screenshots and a video of every feature in the [LeviMC Mods gallery](https://levimc.org/mods/github.com/LiteLDev/BeetrootSkin/?tab=gallery).

### Changed

- A shorter README written for players. Notes for developers (building, the API for other mods) moved to [CONTRIBUTING.md](CONTRIBUTING.md#development).

## [0.1.0] - 2026-10-24

First release.

### Added

- **Food values in tooltips**: the hunger (shanks) and saturation a food restores, drawn with AppleSkin's icons.
  - Foods with harmful effects (rotten flesh, raw chicken, ...) use the "bad food" icons.
  - Shown always by default, or only while `Shift` is held.
- **Hunger and saturation restored preview**: while you hold food (main hand, or offhand), the hunger bar flashes the shanks and saturation that eating it would add.
- **Saturation overlay**: your current saturation as golden outlines over the hunger bar.
- **Exhaustion underlay**: a bar under the hunger bar that fills up as exhaustion builds toward the next point of saturation or hunger being used.
  - Hidden in creative and spectator mode and whenever the game hides the hunger bar.
- **Health restored preview**: while you hold food, the hearts flash the health eating it would restore, using Bedrock's rules:
  - natural regeneration from the new hunger and saturation;
  - the Regeneration effect of foods such as golden apples;
  - hidden on Peaceful and when the `naturalregeneration` game rule is off.
- **Debug info**: AppleSkin's `hunger: N, sat: #.##, exh: 0.00/4` line at the top left of the HUD.
  - `F6` shows or hides it and saves the setting.
  - The key can be remapped in *Settings → Keyboard & Mouse*.
- **Vanilla animations**: the overlays follow the vanilla hunger-bar and low-health jitter (or stay still, with `showVanillaAnimationsOverlay` off).
- **Multiplayer**: client-only; exact values from the integrated server in single-player and LAN worlds you host, the values the server syncs to the client on dedicated servers and joined worlds.
- **Configuration** in `mods/BeetrootSkin/config/config.json` with AppleSkin's option names.
  - Edits apply within about a second while the game runs.
  - Invalid JSON keeps the current settings and leaves the file untouched.
- **API** for other LeviLamina mods, a port of AppleSkin's:
  - `FoodValuesEvent` changes the food values every display uses (tooltips then show default vs modified);
  - `TooltipOverlayEvent::{Pre, Render}` and `HUDOverlayEvent::{Exhaustion, Saturation, HungerRestored, HealthRestored}` hide or move the overlays;
  - headers and import library in `beetrootskin-sdk-client-windows-x64.zip`.
- **Translations**: English and Simplified Chinese.

[Unreleased]: https://github.com/MiracleForest/BeetrootSkin/compare/v0.2.0-beta.1...HEAD
[0.2.0-beta.1]: https://github.com/MiracleForest/BeetrootSkin/compare/v0.1.2...v0.2.0-beta.1
[0.1.2]: https://github.com/MiracleForest/BeetrootSkin/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/MiracleForest/BeetrootSkin/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/MiracleForest/BeetrootSkin/releases/tag/v0.1.0

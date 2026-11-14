# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-11-14

First release.

### Added

- **Food values in tooltips**: the hunger (shanks) and saturation a food restores.
  - Foods with harmful effects (rotten flesh, raw chicken, ...) use the "bad food" icons.
  - Shown always by default, or only while `Shift` is held.
- **Hunger and saturation restored preview**: while you hold food (main hand or offhand), the hunger bar flashes the shanks and saturation that eating it would add.
- **Health restored preview**: while you hold food, the hearts flash the health eating it would restore, following Bedrock's rules:
  - natural regeneration from the new hunger and saturation;
  - the Regeneration effect of foods such as golden apples;
  - hidden on Peaceful and when the `naturalregeneration` game rule is off.
- **Saturation overlay**: your current saturation as golden outlines over the hunger bar.
- **Exhaustion underlay**: a strip behind the hunger bar that fills up as exhaustion builds toward the next point of saturation or hunger being used.
  - Hidden in creative and spectator mode and whenever the game hides the hunger bar.
- **Debug info**: a `hunger: N, sat: #.##, exh: 0.00/4` line at the top left of the HUD.
  - `F6` shows or hides it and saves the setting; the key can be remapped in *Settings → Keyboard & Mouse*.
- **Vanilla animations**: the overlays follow the vanilla hunger-bar and low-health jitter (or stay still, with `showVanillaAnimationsOverlay` off).
- **Multiplayer**: client-only; exact values from the integrated server in single-player and LAN worlds you host, and the values the server syncs to the client on dedicated servers and joined worlds.
- **Configuration** in `mods/BeetrootSkin/config/config.json`.
  - Edits apply within about a second while the game runs.
  - Invalid JSON keeps the current settings and leaves the file untouched.
- **Support for two LeviLamina lines**: Minecraft 1.26.60 with LeviLamina 26.60.x (the default variant, also `26_60`) and Minecraft 1.26.51 with LeviLamina 26.51.x (variant `26_51`), installable from LeviLauncher.
  - Downloads per line: `beetrootskin-client-win-x64-ll26.60.zip` and `beetrootskin-client-win-x64-ll26.51.zip`; extract one into `mods/BeetrootSkin/`.
  - Settings in `mods/BeetrootSkin/config/` are kept across updates.
- **API** for other LeviLamina mods:
  - `FoodValuesEvent` changes the food values every display uses (tooltips then show default vs modified);
  - `TooltipOverlayEvent::{Pre, Render}` and `HUDOverlayEvent::{Exhaustion, Saturation, HungerRestored, HealthRestored}` hide or move the overlays;
  - headers and import library in `beetrootskin-sdk-client-win-x64-ll26.60.zip` and `beetrootskin-sdk-client-win-x64-ll26.51.zip`.
- **Translations**: English and Simplified Chinese.

[Unreleased]: https://github.com/MiracleForest/BeetrootSkin/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/MiracleForest/BeetrootSkin/releases/tag/v0.1.0

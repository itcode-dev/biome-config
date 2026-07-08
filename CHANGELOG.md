# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added

- `@itcode-dev/biome-config/2.4` preset, frozen to the Biome `2.4.x` rule schema.
- `no-nursery` variant for every preset (`@itcode-dev/biome-config/no-nursery`, `/2.4/no-nursery`, `/2.2.0/no-nursery`) that disables the entire `nursery` rule category, so upgrades don't break your config when Biome renames, promotes, or removes nursery rules.
- Korean translation of the README (`README.ko.md`).

### Changed

- Bumped the `@biomejs/biome` devDependency to `^2.5.2` and updated the `latest` preset (`.`) to match the Biome `2.5.2` rule schema.
- Renamed the internal preset files from `biome.jsonc` to `biome-base.jsonc` so Biome's automatic nested-configuration discovery no longer treats each versioned snapshot as its own workspace root (this was causing `biome check`/the language server to crash or hang in this repo).
- Renamed the `src/2.2.0` directory to `src/2.2` internally. The public `@itcode-dev/biome-config/2.2.0` export path is unchanged.

### Fixed

- Fixed `package.json` `exports`/`main` pointing at stale file paths after the internal rename above.
- Fixed the `no-nursery` presets' `extends` field pointing at a file that no longer existed.

## [1.0.1] - 2026-05-18

### Fixed

- Fixed the `files` glob in `package.json` (`src/*.jsonc` → `src/**/*.jsonc`), which failed to include the nested `src/2.2.0/biome.jsonc` preset in the published package.

## [1.0.0] - 2026-05-15

### Added

- `@itcode-dev/biome-config/2.2.0` preset, frozen to the Biome `2.2.x` rule schema.

### Changed

- Bumped the `@biomejs/biome` devDependency to `2.4.x` and restructured the preset: the previously single `src/biome.jsonc` became `src/latest/biome.jsonc` (tracking the newest Biome release) plus the frozen `2.2.0` snapshot above.

## [0.1.0] - 2025-08-29

### Added

- Initial publishable package setup: `exports`, `main`, and `files` fields in `package.json`.

## [0.0.0] - 2025-08-29

### Added

- Initial Biome configuration preset.

[Unreleased]: https://github.com/itcode-dev/biome-config/compare/1.0.1...HEAD
[1.0.1]: https://github.com/itcode-dev/biome-config/compare/1.0.0...1.0.1
[1.0.0]: https://github.com/itcode-dev/biome-config/compare/0.1.0...1.0.0
[0.1.0]: https://github.com/itcode-dev/biome-config/compare/0.0.0...0.1.0

# @itcode-dev/biome-config

[한국어](./README.ko.md)

Shared [Biome](https://biomejs.dev) configuration presets for itcode.dev projects. Every rule in the preset is annotated with a comment explaining why it's turned on, off, or tuned the way it is, so the config doubles as documentation.

> [!NOTE]
> - This configuration is built around fairly personal preferences, so some parts of it don't align with common/universal conventions.
> - Every option is explicitly specified rather than left to defaults, which makes the configuration somewhat rigid.
> - It was primarily developed for reuse across the author's own personal projects.

## Installation

```bash
pnpm add -D @itcode-dev/biome-config @biomejs/biome
```

```bash
npm install -D @itcode-dev/biome-config @biomejs/biome
```

## Usage

Extend the preset from your project's `biome.jsonc`:

```jsonc
{
	"$schema": "https://biomejs.dev/schemas/2.5.2/schema.json",
	"extends": ["@itcode-dev/biome-config"]
}
```

## Available presets

| Export | Biome version | Description |
| --- | --- | --- |
| `@itcode-dev/biome-config` | latest | Tracks the newest supported Biome release. Rules move as Biome's own categories change (e.g. `nursery` rules get promoted or removed). |
| `@itcode-dev/biome-config/2.4` | `2.4.x` | Frozen preset matching the Biome `2.4` rule schema. |
| `@itcode-dev/biome-config/2.2.0` | `2.2.x` | Frozen preset matching the Biome `2.2` rule schema. |

Pick a frozen (`/2.x`) export if you want your lint rules to stay stable across Biome upgrades instead of shifting every time `@itcode-dev/biome-config` is updated to track a newer Biome release.

### `nursery` rules

Biome's `nursery` category holds experimental rules that get renamed, promoted to a stable category, or removed between releases. That churn can break your config the moment either Biome or this package is upgraded. If you'd rather not deal with that, use the `no-nursery` variant of any preset above, which disables the entire `nursery` category:

```jsonc
{
	"$schema": "https://biomejs.dev/schemas/2.5.2/schema.json",
	"extends": ["@itcode-dev/biome-config/no-nursery"]
}
```

Every preset has a matching `no-nursery` export: `@itcode-dev/biome-config/no-nursery`, `@itcode-dev/biome-config/2.4/no-nursery`, `@itcode-dev/biome-config/2.2.0/no-nursery`.

## Conventions

- Indentation: tabs (width 4)
- Line width: 128
- Line endings: LF
- Quotes: single quotes in JS/TS, double quotes in JSX and CSS
- Semicolons: always
- Trailing commas: none

These and every linter rule can be overridden in your own `biome.jsonc` after extending this preset.

## Compatibility

This package requires `@biomejs/biome` `^2.2.0` or later as a peer dependency. Match the preset you extend from to the Biome version installed in your project (see the table above).

## License

[Apache-2.0](./LICENSE)

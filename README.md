# STConfig

Sublime Text configuration/settings editor. Runs as a standalone Sublime Text
package: an in-editor command opens an in-process HTTP server + browser UI for
browsing and editing ST's keybindings/commands/menus (`st_config.py`, v1) and,
more fully, ST settings with byte-faithful JSON5 round-tripping
(`settings_editor.py`, v2, Eclipse property-sheet style). See
`EDITOR_DESIGN.md` for the design rationale and data model.

`lib/` vendors a pure-Python `json5` parser (which itself vendors `sly`, a
lexer/parser generator) so settings files can be read and rewritten without
losing comments, trailing commas, or formatting on untouched lines.

Extracted from the [SText](https://github.com/dpc00/SText) package — this
component had no code-level dependency on SText's AI/logging pieces, so it
lives on its own.

## Deploy

Sublime Text auto-loads top-level `.py` files in each `Packages/<name>/`
folder as plugins, so this repo installs by copying (or symlinking) itself
into `Packages/STConfig`:

- Windows: `%APPDATA%\Sublime Text\Packages\STConfig`
- macOS: `~/Library/Application Support/Sublime Text/Packages/STConfig`
- Linux: `~/.config/sublime-text/Packages/STConfig`

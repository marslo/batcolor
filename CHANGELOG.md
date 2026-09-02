## [1.1.3](https://github.com/marslo/batchip/compare/v1.1.2...v1.1.3) (2026-09-02)

### Bug Fixes

* run bat by absolute path instead of 'command' builtin ([48b6ca8](https://github.com/marslo/batchip/commit/48b6ca82d26c2c0e13b89597ffe15d26b1d409f3))
  - point _batcmd at "$(type -P bat)" instead of `command bat`
  - exec the resolved bat binary for --help/--version/--list-*/cache passthrough
  - add NOTE explaining the `command` builtin can't be exec'd by env/exec

## [1.1.2](https://github.com/marslo/batchip/compare/v1.1.1...v1.1.2) (2026-06-11)

### fix

* fix(core): honor bat config/env in wrapper mode, keep plain only for pipe mode
  - forced `BAT_STYLE=plain` for pipe mode only


### docs

* docs: update readme

## [1.1.1](https://github.com/marslo/batchip/compare/v1.1.0...v1.1.1) (2026-06-02)

### fix

* fix(hexcode): fix the end boundary of hexcode

Fixed #4

## [1.1.0](https://github.com/marslo/batchip/compare/v1.0.2...v1.1.0) (2026-06-02)

### feat

* feat(oklch): add support for oklch

### ci

* ci: fix the 'Node.js 20 actions are deprecated' issue in pre-commit workflow

### docs

* docs: fix typo

## [1.0.2](https://github.com/marslo/batchip/compare/v1.0.1...v1.0.2) (2026-05-19)

### Code Refactoring

* refactor(rename): rename to batchip ( from batcolor )
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Documentation

* docs: update readme
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Bug Fixes

* fix(core): fixed the double ANSI escape rendering in pipe mode

Fixed #3
Signed-off-by: marslo <marslo.jiao@gmail.com>
* fix(core): optimize pipe mode to bypass bat and its env vars
  - color filter directly WITHOUT `bat` when stdin is piped and no args given - `cat file | batchip`
  - skip BAT_OPTS/BAT_STYLE env manipulation in pipe mode, since the options might be provided by bat previously - `bat -p --color always file | batchip`
  - add github actions pre-commit workflow

Fixed #1

Signed-off-by: marslo <marslo.jiao@gmail.com>

## [1.0.1](https://github.com/marslo/batcolor/compare/v1.0.0...v1.0.1) (2026-05-17)

### Documentation

* docs: update README.md and add screenshots
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Others

* chore: introduce pre-commit hook
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Bug Fixes

* fix(core): resolve pipe rendering and preserve native bat highlights
  - suppress phantom line numbers during pipe input (! -t 0) by stripping global BAT_OPTS and enforcing `BAT_STYLE=plain` via `env` command
  - refactor `_color_filter` Perl regex to safely inject background ANSI codes without stripping bat's native foreground syntax highlighting
  - restore Rec. 709 luma algorithm to dynamically set text to black or white for readability inside color blocks
  - prevent color bleed into subsequent text by replacing the hardcoded trailing color with a standard reset (`\033[39;49m`)

Fixed #1

Signed-off-by: marslo <marslo.jiao@gmail.com>

## 1.0.0 (2026-05-16)

### Features

* feat(init): init the batcolor
  Signed-off-by: marslo <marslo.jiao@gmail.com>

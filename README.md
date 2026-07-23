# shellcheck

A [Dagger](https://dagger.io) module that lints shell scripts with
[ShellCheck](https://www.shellcheck.net).

## Functions

| Function  | Description                                                     |
| --------- | --------------------------------------------------------------- |
| `check`   | Run shellcheck on every visible shell script (a `@check`).      |
| `scripts` | The discovered scripts as `Script` objects, each individually checkable. |
| `base`    | The container with shellcheck installed.                        |

## Usage

Install the module in your workspace:

```sh
dagger install github.com/dagger/shellcheck
```

Run the check:

```sh
dagger check                    # run every check in the workspace
dagger check shellcheck:check   # just the shellcheck check
```

## Working directory awareness

Script discovery finds `**/*.sh` at or below your current working directory,
so running from a subdirectory checks only that subtree; script paths are
reported relative to it.

Each script is checked in its own container, so results are cached per
script — editing one script only re-checks that script.

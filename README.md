# prenv

`prenv` is a small Bash CLI for inspecting and formatting shell environment data.

## What it does

- Pretty-prints environment variables
- Shows `PATH` entries one per line
- Runs a basic environment health check
- Includes an intended `diff` mode for comparing environment state before and after a command

## Usage

Because the script is not executable yet, run it with Bash:

```bash
bash ./prenv
```

If you want to run it as `./prenv`, make it executable first:

```bash
chmod +x ./prenv
./prenv
```

## Commands

### `print`

Pretty-print the current environment. This is the default command.

```bash
bash ./prenv
bash ./prenv print
```

Useful options:

- `--sort` sorts variables alphabetically
- `--filter <text>` filters variables by key or value
- `--wrap` wraps long values instead of truncating them
- `--width <n>` changes the output width
- `--no-color` disables ANSI colors

Examples:

```bash
bash ./prenv --sort
bash ./prenv --filter PATH
bash ./prenv --filter aws --width 100
bash ./prenv --wrap
```

### `path`

Print the current `PATH` as a numbered list.

```bash
bash ./prenv path
```

### `doctor`

Show a lightweight environment summary, including:

- shell
- user
- home directory
- AWS CLI presence and active profile
- `kubectl` presence
- Node.js version
- total number of `PATH` entries

```bash
bash ./prenv doctor
```

### `diff`

Intended to compare environment state before and after running a command.

```bash
bash ./prenv diff 'npm run build'
```

## Examples

```bash
# Show all variables
bash ./prenv

# Show only variables related to PATH
bash ./prenv --filter PATH

# Show variables in sorted order
bash ./prenv --sort

# Inspect PATH cleanly
bash ./prenv path

# Run environment checks
bash ./prenv doctor
```

## Current caveats

- The script currently needs `bash ./prenv` unless you add execute permissions.
- `diff` is present in the interface, but its current argument parsing and subshell behavior need follow-up before it works as expected for command-driven environment changes.

## Help

```bash
bash ./prenv --help
```

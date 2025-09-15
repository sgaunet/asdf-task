# asdf-task

[![Build](https://github.com/sgaunet/asdf-task/actions/workflows/build.yml/badge.svg)](https://github.com/sgaunet/asdf-task/actions/workflows/build.yml)
[![Lint](https://github.com/sgaunet/asdf-task/actions/workflows/lint.yml/badge.svg)](https://github.com/sgaunet/asdf-task/actions/workflows/lint.yml)

[Task](https://github.com/go-task/task) plugin for the [asdf version manager](https://asdf-vm.com).

Task is a task runner / build tool that aims to be simpler and easier to use than, for example, GNU Make.

## Contents

- [asdf-task](#asdf-task)
  - [Contents](#contents)
  - [Dependencies](#dependencies)
  - [Install](#install)
    - [Plugin](#plugin)
    - [Task](#task)
  - [Environment Variables](#environment-variables)
  - [Features](#features)
  - [Contributing](#contributing)
    - [Development](#development)
    - [Testing Locally](#testing-locally)
    - [Credits](#credits)
  - [License](#license)

## Dependencies

**Required:**
- `bash` (3.2+), `curl`, `tar`, `git`
- [POSIX utilities](https://pubs.opengroup.org/onlinepubs/9699919799/idx/utilities.html)

**Optional:**
- `sha256sum` or `shasum` - For checksum verification
- `df` - For disk space checking

## Install

### Plugin

```shell
asdf plugin add task
# or
asdf plugin add task https://github.com/sgaunet/asdf-task.git
```

### Task

```shell
# Show all installable versions
asdf list-all task

# Install specific version
asdf install task latest

# Set a version globally (on your ~/.tool-versions file)
asdf global task latest

# Now task commands are available
task --version

# Get help
asdf help task
```

Check the [asdf documentation](https://asdf-vm.com/guide/getting-started.html) for more instructions on how to install & manage versions.

## Environment Variables

The plugin supports several environment variables for customization:

| Variable | Default | Description |
|----------|---------|-------------|
| `ASDF_TASK_DEBUG` | `0` | Enable debug output for troubleshooting |
| `ASDF_TASK_MAX_RETRIES` | `3` | Maximum retry attempts for network operations |
| `ASDF_TASK_RETRY_DELAY` | `2` | Delay in seconds between retries |
| `GITHUB_API_TOKEN` | - | GitHub token for higher API rate limits |

## Features

- ✅ **Automatic retries** - Network operations are retried on failure
- ✅ **Checksum verification** - Downloads are verified when checksums are available
- ✅ **Progress indicators** - Visual feedback during downloads
- ✅ **Debug mode** - Detailed logging for troubleshooting
- ✅ **Platform detection** - Automatic detection of OS and architecture
- ✅ **Disk space checking** - Verifies available space before installation
- ✅ **Multi-platform support** - Linux, macOS, Windows (WSL), BSD variants
- ✅ **Architecture support** - amd64, arm64, 386, arm

## Contributing

Contributions of any kind are welcome! See the [contributing guide](CONTRIBUTING.md).

### Development

This project uses Task for automation:

```shell
# List available tasks
task

# Format code
task format

# Run linting
task lint

# Run tests
task test
```

### Testing Locally

```shell
asdf plugin test <plugin-name> <plugin-url> [--asdf-tool-version <version>] [--asdf-plugin-gitref <git-ref>] [test-command*]

asdf plugin test task https://github.com/sgaunet/asdf-task "task --version"
```

Tests are automatically run in GitHub Actions on push and PR.

### Credits

[Thanks goes to these contributors](https://github.com/sgaunet/asdf-task/graphs/contributors)!

## License

See [LICENSE](LICENSE)

# Repository Updater and Build Executor Module

This module facilitates updating the local repository and executing build instructions. It contains a class `Updater` designed for these purposes.

## Overview

The `Updater` class in this module provides functionality to check if the current branch is behind the remote repository, pull updates from the remote, and execute build instructions defined in the 'build.updater' file.


## Classes

### Updater

A class for updating the local repository and executing build instructions.

#### Methods

- `__init__()`: Initializes the updater object.
- `run_shell_command(command_list: list) -> bool`: Executes a shell command using subprocess.
- `check_for_update() -> bool`: Checks if the local branch is behind the remote branch.
- `pull_from_remote() -> None`: Pulls updates from the remote repository.
- `run_build() -> bool`: Executes build instructions from the 'build.updater' file.

## Build File Configuration

Build instructions are expected to be defined in the 'build.updater' file. Each line in this file represents a separate command, prefixed with keywords to specify the command type:
- `python`: Command to be run in the Python environment.
- `shell`: Command to be run in the system shell.

For example:
```
shell rm -rf .
python print('Repo cleared')
shell python3 build.py
python print('Build process has run')
```


## Usage

Ensure that the 'build.updater' file contains the necessary build instructions. Then, execute the module to automatically check for updates, pull from the remote if necessary, and run the build instructions.

```python
if __name__ == '__main__':
    updater = Updater()
    if updater.check_for_update():
        updater.pull_from_remote()
        updater.run_build()
```
Note: Ensure proper configuration and permissions for executing shell commands.

## Dependencies
`subprocess`: For running shell commands.

License
This module is released under the MIT License.

Feel free to adjust the README according to your project's specifications and requirements.

# Repository Updater and Build Executor

This module provides functionality for updating a local repository and executing build instructions. It contains a class `Updater` that automates the process of checking for updates from a remote repository, pulling changes if necessary, and executing build instructions specified in a designated file.

## Usage

To use this module, follow these steps:

1. Ensure that the `build.updater` file is present in the repository. This file should contain the build instructions, with each command starting with either `python` or `shell`.
2. Import the `Updater` class from the module.
3. Instantiate an `Updater` object.
4. Call the `run_update_sequence()` method to perform the update and build process.

```python
from repository_updater import Updater

# Instantiate build file path
Updater.build_file_path = 'path to your file'


# Run update sequence
Updater.run_update_sequence()
```

## Build File Format
The build.updater file should contain build instructions, with each command specified on a separate line. Each command should start with one of the following keywords:

- `python`: Indicates that the command should be executed in the Python environment.
- `shell`: Indicates that the command should be executed in the command shell.

### Example build.updater file:
```bash
shell rm -rf .
python print('Repository cleared')
shell python3 build.py
python print('Build process executed')
```

## Class: Updater
### Methods
- `run_update_sequence()`: Checks if the current branch is behind the remote repository, pulls changes if necessary, and executes build instructions.
- `run_build()`: Reads the build instructions from `Updater.build_file_path` and executes them.
- `pull_from_remote()`: Pulls changes from the remote repository using git pull.
- `check_for_update()`: Checks if the current branch is behind the remote repository.

## Requirements
- Python 3.x
- Git

## License
This project is licensed under the MIT License - see the LICENSE file for details.
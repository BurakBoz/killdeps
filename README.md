# killdeps

![Build Status](https://travis-ci.com/burakboz/killdeps.svg?branch=main)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![PHP](https://img.shields.io/badge/php-%5E8.0-blue)

**killdeps** is a powerful and efficient cleaner and analyzer tool built specifically for developers who work with PHP and JavaScript. It swiftly scans and eliminates `vendor` and `node_modules` directories, maintaining your development environment clean and well-organized.

## Features

- Swift and effective scanning of `vendor` and `node_modules` directories.
- Secure elimination of unnecessary directories.
- Comprehensive analysis of your project's environment.
- User-friendly command-line interface.
- Compatible with PHP 8+ and all modern JavaScript environments.
- No dependency on third-party libraries.
- Supports bun, yarn, npm lock files

## Installation

To install **killdeps**, ensure that PHP 8.0 or higher and Composer are installed on your system.

### Installation in a project
```bash
composer require burakboz/killdeps
```

#### How to run with composer?
```bash
# run via composer
composer killdeps -- --dry-run .
composer killdeps -- --help

# an alternative way
composer run-script killdeps -- --dry-run .
composer run-script killdeps -- --help
```

---

### Installation on Windows using `composer`

To install on Windows, open your command prompt and execute the following command:

```bash
composer global require burakboz/killdeps
```

To add the `~/.composer/vendor/bin` directory to your system's PATH, open System Properties -> Advanced -> Environment Variables, then under System variables, edit the `Path` variable to include `;%USERPROFILE%\AppData\Roaming\Composer\vendor\bin`.

---

### Installation on Windows using `PowerShell`

```bash
# Download the killdeps script
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/burakboz/killdeps/master/bin/killdeps" -OutFile "killdeps"

# Check if the ~/bin directory exists, create it if not
If(!(Test-Path "$env:USERPROFILE\bin"))
{
    New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\bin"
}

# Move the downloaded script to the ~/bin directory
Move-Item -Path .\killdeps -Destination "$env:USERPROFILE\bin"

# Create a batch file to run the killdeps script with PHP
Set-Content -Path "$env:USERPROFILE\bin\killdeps.bat" -Value "php %USERPROFILE%\bin\killdeps %*"

# Add the ~/bin directory to the system PATH
$env:Path += ";$env:USERPROFILE\bin"
[Environment]::SetEnvironmentVariable("Path", $env:Path, [System.EnvironmentVariableTarget]::User)
```

### Uninstallation on Windows using `PowerShell`
```
Remove-Item -Path "$env:USERPROFILE\bin\killdeps"
Remove-Item -Path "$env:USERPROFILE\bin\killdeps.bat"
```
---

### Installation on Linux / macOS using `composer`

To install on Linux or macOS, open your terminal and execute the following command:

```bash
composer global require burakboz/killdeps
```

To add the `~/.composer/vendor/bin` directory to your system's PATH, modify your shell profile file (e.g., `~/.bashrc`, `~/.bash_profile`, or `~/.zshrc`) and add this line:

```bash
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

Afterwards, run `source ~/.bashrc` (or the appropriate profile file for your shell) to update your current session.

### Installation on Linux / macOS without composer

```bash
cd ~;(wget --no-check-certificate https://raw.githubusercontent.com/burakboz/killdeps/master/bin/killdeps -O killdeps || curl -LJO https://raw.githubusercontent.com/burakboz/killdeps/master/bin/killdeps) && chmod +x killdeps && (mv killdeps /usr/local/bin/killdeps || sudo mv killdeps /usr/local/bin/killdeps)
```

### Uninstallation on Linux / macOS

```bash
(rm -f /usr/local/bin/killdeps || sudo rm -f /usr/local/bin/killdeps)
```

## Usage

To execute **killdeps**, navigate to the directory you wish to clean and type:

```bash
killdeps .
```

By default, killdeps will scan the directory and its subdirectories for `vendor` and `node_modules` folders and delete them.


## Examples

```bash
killdeps --help
# Show help

killdeps . 
# Deletes vendor and node_modules folders in the current directory

killdeps D:
# Deletes vendor and node_modules folders in the D: drive

killdeps --dry-run .
# Displays which folders would be deleted and the amount of space that could be reclaimed

killdeps --only-locked .
# If a lock file exists along with composer.json or package.json file, delete the associated package folder.

killdeps --only-locked --dry-run .
# Show locked package folders and reclaimable space

php killdeps
# Run directly with php interpreter
```

## Contributing

We welcome contributions, issues, and feature requests! Feel free to check the [issues page](https://github.com/burakboz/killdeps/issues).

## License

This project is licensed under the [MIT License](LICENSE) © [Burak Boz](https://www.burakboz.net)

## To Do:

- [x] Implement fast scan and delete for `vendor` & `node_modules` folders.
- [x] Implement dry-run feature to simulate deletion.
- [ ] Improve logging and output information.
- [ ] Add unit tests for core functionality.
- [ ] Update documentation and examples.

## Contact

For any questions or suggestions to improve killdeps, please feel free to contact me at killdeps@burakboz.net.

# RocUp - the tool for managing your Roc compiler installation

RocUp is a tool for managing your Roc compiler installation. It allows you to install locally the latest version of the Roc compiler, and to switch between different locally installed versions.

## Installation

To install RocUp, you can use the following command:

```bash
mkdir -p ~/.rocup

curl -sSL https://raw.githubusercontent.com/roc-lang/rocup/master/rocup > ~/.rocup/rocup
```

## Running RocUp

To run RocUp, you can use the following command:

```bash
$ cd ~/.rocup
./rocup
```

This will:

- download the latest version of the Roc compiler
- install it locally in the `~/.rocup` directory
- create a symbolic link to the Roc compiler in the `~/.rocup/roc` directory
- (sudo priviledges required) create a symbolic links for `roc` and `roc_language_server` in `/usr/local/bin` to the compiler installed in the `~/.rocup/roc` directory

## Example usage

Executing the `rocup` command will download the latest version of the Roc compiler and install it locally with symbolic links created. The output will look like this:

```terminal
~/.rocup> ./rocup
.. apple silicon mac detected
.. downloading latest release of the Roc compiler
.. extracting: roc_nightly-macos_apple_silicon-latest.tar.gz
.. installing nth latest local version (n = 1)

.. selected locally available versions
======================================
 ->  roc_nightly-macos_apple_silicon-2024-05-13-e5ea6dc4617/roc

.. creating local symlink to latest downloaded version
roc nightly pre-release, built from commit e5ea6dc4617 on Mon May 13 10:47:45 UTC 2024
```

Over time, you will have more than one version of the Roc compiler downloaded locally in `.rocup` directory. You can switch between them using the following command (for example, to switch to the second latest version):

```terminal

~/.rocup> ./rocup 2
.. apple silicon mac detected
.. downloading latest release of the Roc compiler
.. extracting: roc_nightly-macos_apple_silicon-latest.tar.gz
.. installing nth latest local version (n = 2)

.. selected locally available versions
======================================
     roc_nightly-macos_apple_silicon-2024-05-13-e5ea6dc4617/roc
 ->  roc_nightly-macos_apple_silicon-2024-05-11-dd9a6ff2e4a/roc

.. creating local symlink to latest downloaded version
.. creating symlinks in /usr/local/bin
roc nightly pre-release, built from commit dd9a6ff2e4a on Sat May 11 09:12:29 UTC 2024
```
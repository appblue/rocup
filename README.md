# RocUp - the tool for managing your Roc compiler installation

RocUp is a tool for managing your Roc compiler installation. It allows you to install locally the latest version of the Roc compiler, and to switch between different locally installed versions.

Please note that this tool assumes that you have `curl` and `tar` installed on your system, and that you have `sudo` privileges to create symbolic links in `/usr/local/bin` directory. There is all an assumption that `/usr/local/bin` is in your PATH for the Roc compiler to be available from anywhere in your terminal.

**WARNINGS**

* RocUp is attempting to overwrite `roc` and `roc_language_server` binaries in `/usr/local/bin` directory. If you have other versions of Roc compiler installed in `/usr/local/bin` or other tools named the same, they will be overwritten.

* RocUp is a pre-release tool and is not yet fully tested. Please use it at your own risk.


**Note 1:** At the moment RocUp does not allow to download older versions of the Roc compiler. It only allows to download the latest version of the Roc compiler, but keeps all downloaded versions locally in the `~/.rocup` directory, and allows switching back and forth between them.

**Note 2:** RocUp is currently only available for macOS (Silicon and Intel based machines) and Linux (x86_64).

## Installation

To install RocUp, you can use the following command:

```bash
mkdir -p ~/.rocup
curl -sSL https://raw.githubusercontent.com/appblue/rocup/master/rocup > ~/.rocup/rocup
chmod a+x ~/.rocup/rocup
```

## Running RocUp

To run RocUp, you can use the following command:

```bash
$ ~/.rocup/rocup
```

This will:

- download the latest version of the Roc compiler
- install it locally in the `~/.rocup` directory
- create a symbolic link to the Roc compiler in the `~/.rocup/roc` directory
- (sudo priviledges required) create a symbolic links for `roc` and `roc_language_server` in `/usr/local/bin` to the compiler installed in the `~/.rocup/roc` directory

If you add `.rocup` directory to your PATH, you can run `rocup` from anywhere in your terminal.

## Example usage

Executing the `rocup` command will download the latest version of the Roc compiler and install it locally with symbolic links created. The output will look like this:

```terminal
$ ~/.rocup/rocup
.. apple silicon mac detected
.. downloading latest release of the Roc compiler
.. extracting: roc_nightly-macos_apple_silicon-latest.tar.gz
.. installing nth latest local version (n = 1)

.. selected locally available versions
   -----------------------------------
 ->  /Users/krzysztof.kielak/.rocup/roc_nightly-macos_apple_silicon-2024-05-13-e5ea6dc4617/roc

.. creating local symlink to latest downloaded version
.. attempting to create symlinks in /usr/local/bin
.. are you sure you want to overwrite roc and roc_language_server in /usr/local/bin? [y/N] y

.. installation complete
.. .. roc compiler is now available in /usr/local/bin/roc
.. .. roc language server is now available in /usr/local/bin/roc_language_server
.. .. roc compiler version: roc nightly pre-release, built from commit e5ea6dc4617 on Mon May 13 10:47:45 UTC 2024
```

Over time, you will have more than one version of the Roc compiler downloaded locally in `.rocup` directory. You can switch between them using the following command (for example, to switch to the second latest version):

```terminal
$ ~/.rocup/rocup 2
.. apple silicon mac detected
.. downloading latest release of the Roc compiler
.. extracting: roc_nightly-macos_apple_silicon-latest.tar.gz
.. installing nth latest local version (n = 2)

.. selected locally available versions
   -----------------------------------
     /Users/krzysztof.kielak/.rocup/roc_nightly-macos_apple_silicon-2024-05-13-e5ea6dc4617/roc
 ->  /Users/krzysztof.kielak/.rocup/roc_nightly-macos_apple_silicon-2024-05-11-dd9a6ff2e4a/roc

.. creating local symlink to latest downloaded version
.. installation complete
.. .. roc compiler is now available in /usr/local/bin/roc
.. .. roc language server is now available in /usr/local/bin/roc_language_server
.. .. roc compiler version: roc nightly pre-release, built from commit dd9a6ff2e4a on Sat May 11 09:12:29 UTC 2024
```

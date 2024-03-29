# Workflow

_This section explains how Tree-of-Life operates_

Tree-of-Life aims to be platform independent; because it is written in Python, it should run where ever Python can run, Python itself provides an excellent interface between developers and the different OS platforms. Tree-of-Life is written fully in Python an is compatible with Python 2.7 and 3.x series. We consider safe to rely on Python because nowadays virtually every computer *(within our scope)* has Python installed; installing Python from scratch in the user's computer lies outside this project's scope.

Tree-of-Life is designed to serve [Python-based or Python-dependent](#note) projects. It installs a Python distribution (*using* [Miniconda](https://docs.conda.io/en/latest/miniconda.html)) and the required *host* project's Python dependencies in an **encapsulated environment** that resides in the host project unpacked folder. In this way, there is *no* mixing between the software installation and the users system.

Also, its architecture allows the developer to write the project's executable files that are configured accordingly to the project's dependencies and consequently made available for the user after installation.

Read on how to implement Tree-of-Life in your project [here](#implementation).

## The Installation step

The aim of Tree-of-Life is to setup the host project in the users' computer with the minimum effort from the user by providing *double-click* (or *single-run*) installation process, for example:

```
python install_the_software.py
```

or *(depending on the developers choice)*

```
./install_the_software
```

If you are a developer, you are invited to read the [tree_of_life.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/tree_of_life.py) file to understand its workflow from the developer's point of view.

From the user's point of view, the installation workflow is as follows:

1. Queries user if to install the Python-dependencies _automatically_ or _manually_.
    1. If, _automatic_ (recommended):
        1. checks available disk space
        1. checks if previous Miniconda installation exists inside the *host* project folder
        1. Downloads and installs the latest version of Miniconda locally in the project's folder. The Miniconda version to install is derived from the user's platform
        1. installs the project's Python ENV as described in the `yml` file inside the [install](https://github.com/joaomcteixeira/Tree-of-Life/tree/master/install) folder
    1. If, _manual_ (proficient Python users):
        1. warns the user that s/he must install the required dependencies manually. For proficient Python users/devels this should be straight forward as all the information is stored in the `yml` file.
        1. Does NOT install any Python packages
1. Creates the executable files following the [executables.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/executables.py) file
    1. _executable_ files are linked to the project's Python dependencies via _shebang_
    1. the _shebang_ is defined in agreement to the first main query (Miniconda installation step):
        1. if Miniconda and the Python ENV were installed automatically, *shebangs* will point to that env
        1. if the user decided to install the Python dependencies manually, the *shebangs* will point to the system's current Python executable
        1. In _manuall_ installations, _shebangs_ must also be configured by the user to point to the correct Python environment, in case the Pythonista user wants to use *shebangs* at all.
    1. _exec_ files are given executable permissions system wide. If you want to restrict _exec_ files permissions you can alter those after installation.
1. Creates the `installation_vars.py` file. This file registers all installation variables that are required for _updating_ purposes. If this file is removed or altered manually, future *updates* will fail an can compromise the whole installation.
1. All installation output regarding _information_ and _debugging_ is written to a `.log` file.

## Updater

Tree-of-Life provides an _updater_ script to allow the user to keep up to date with the host project's latest version. The _updater_ is part of the executable files and is created during the installation process inside the `bin` folder.

The updater was designed to keep the user's installation up to date with the developers GitHub project. But, by no means it restricts a GitHub repository; by default, the updater simply requires a web link to a ZIP file containing the project. *(for developers)* You can read the _updater_ workflow in the `update_script_code` variable inside [executables.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/executables.py).

From the user's point of view, the update routines are as follow:

1. Downloads the latest version of the software
1. Unpacks it to a temporary folder
1. Removes the previous version (its folders)
  1. files that do not belong to the project but are stored in the main project folder are **not** removed during update.
1. Moves the new version files to the project installation folder
1. If the installation was performed in _automatic_ mode:
    1. checks if the ENV needs to be updated, if yes, updates it
1. Rebuilds the executable files. In this way, these are also updated
1. Rebuilds the `installations_vars.py`
1. All updater output regarding _information_ and _debugging_ purposes is written to a `.log` file.

Read more on the updater script [here](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/docs/Implementation.md#the-updater-script).

## The executable files

By design, Tree-of-Life considers the host project's executable files as Python scripts ([see note](#note)). But, this is definitively not mandatory and can be easily adapted to fit other needs.

Tree-of-Life uses _shebangs_ to point the executable files to the project's Python ENV, that is, to the correct Python interpreter.

For UNIX systems the executable files are created without extension, so that the user is naturally driven to execute them as follows:

```
.bin/exec_1
```

On Windows, executable files are created with the `.py` extension (by default). However, they should not be executed with `$ python exec_1.py`, because in this way the called Python interpreter will prevail in disregard of the _shebang_. You should warn the users to use `$ exec_1.py` directly, so that the system will use the Python ENV pointed by the _shebang_.

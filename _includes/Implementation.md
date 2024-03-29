# Implementation

_How to implement Tree-of-Life DISS on your project_

## The architecture of Tree-of-Life

The architecture of Tree-of-Life is straightforward; I invite you to read through the [tree_of_life.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/tree_of_life.py) script to understand the installation process and its dependencies.

## How to implement Tree-of-Life in your project

### Firstly

Tree-of-Life is composed of a main _installer_ file [tree_of_life.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/tree_of_life.py) and an [install](https://github.com/joaomcteixeira/Tree-of-Life/tree/master/install) folder where all its dependencies and _template_ files are stored. To implement Tree-of-Life in your project copy the _main installer_ file and the `install` folder to your project repository/folder, always according to [the project license](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/LICENSE).

**example:**
```
MyProject/
    -- MyProject_folder/
        -- (... all your project scr files ...)
    
    -- install/
    -- tree_of_life.py (this is the main installer, renamed it at will)
```

### Secondly

*What must be changed to adapt Tree-of-Life to your project:*

#### host project variables

Configure Tree-of-Life according to your project (the host project), it's very easy, simply update the variables in the [host_project_vars.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/host_project_vars.py).

There is also a BIG BANNER at the end which is displayed as advertising header in the beginning of the installation, change it to fit your project if desired.

#### env YML file

The [template_env.yml](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/template_env.yml) file describes the Anaconda Python environment that serves your project and which Tree-of-Life will install; in other words, the Python dependencies of your project, configure it according to your needs.

_Explaining an YML file lies outside this wiki, read the Anaconda's official documentation [here](https://conda.io/docs/user-guide/tasks/manage-environments.html)._

The first line of the [template_env.yml](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/template_env.yml) file, `# version: 1`, serves updating purposes. If in future releases of your project you update its dependencies, you should increase the `yml` version number (`# version: 2`) and the Tree-of-Life _updater_ script will properly update the Miniconda ENV in the user's installation folder.

#### the executables

By design, Tree-of-Life considers the host project's executable files as Python scripts. In the [vision of the project](#vision), if the developer wants to have full control on what the user can do and when, the project's executable files should not be readily available. Instead, executable files should be created during the installation process and properly linked to the Python ENV's executable (dependencies).

To accomplish this, Tree-of-Life is designed such that the executable scripts should be coded as raw strings in the [executables.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/executables.py) file and headed by a formatter sign `#! {}` where the _shebang_ will be inserted. The [executables.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/executables.py) file reads very easily and provides executable templates for you to configure according to your project needs.

### Thirdly

Change the Tree-of-Life library at will but within the LICENSE terms. Some helpful information:

#### the main installer

Feel free to change the main installer name to fit your project requirements, for example, `install_mysoftware.py`.

#### messages.py

The majority of the messages that are displayed during the installation process are organized inside the [messages.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/messages.py) file. Messages and titles can be formatted using the `_formats*` functions. These messages provide a functional template for you to use right away, yet, you can very easily rewrite these messages to properly fit your project.

#### The Updater script

Also, an **updater** script is provided in the [executables.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/executables.py). The updater is ready-to-use as long as the related variables in [host_project_vars.py](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/host_project_vars.py) are configured according to the host project.

### License headers

Alter the license headers according to [this project license](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/LICENSE) so that a reference to the official work is made and the changes you have implemented are identified. Suggestions:

```
THIS FILE WAS ADAPTED FROM TREE-OF-LIFE PROJECT (version 1.1.2 - LGPLv3)
AND MODIFIED ACCORDINGLY TO THE NEEDS OF THE <your project name> PROJECT.

Visit the original Tree-of-Life project at:

https://github.com/TreeOfLife-diss
```

Let us know if you implement Tree-of-Life in your project, we would love to add it to our list in the main README file. `:-)`

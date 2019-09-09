## Solving the problem

### the installer

**Tree-of-Life** is a simple and universal platform that automatically configures the required Python dependencies and executable files for your Python-based project - thus bridging the gap between developers and users. Therefore, to install a project that hosts Tree-of-Life, the users must simply type:

```
python tree_of_life.py
```

#### Python to solve Python

Python itself provides an excellent interface between developers and the different OS platforms, therefore, Tree-of-Life is written fully in Python an is compatible with Python 2.7 and 3.x series. I consider safe to rely on Python because nowadays (year 2018) virtually every computer has Python installed and the above command can be executed straightforwardly; installing Python from scratch in the user's computer lies outside this project.

### the updater

Tree-of-Life provides also an independent updater that can be used by users to maintain their project's installation up to date, without requiring Git or performing any other task outside those provided by the project. The UPDATER script is created during the installation.

## User interface

When running the installation script (`tree_of_life.py`) the user will be prompt with two installation routines: **automatic** and **manual**. 
 
- The _automatic_ (recommended) option will install a [Miniconda](https://conda.io/miniconda.html) distribution in the project's folder with all the required Python libraries, this Miniconda installation will **not** conflict with the user system's Python installation. Also, the executable files will be configured accordingly.
- The _manual_ installation will create TEMPLATE executable files. The user should manually configure all the required Python libraries as well as the compatibility between the executable files and the Python dependencies, for example via _shebangs_. Users can use the [template_env.yml](https://github.com/joaomcteixeira/Tree-of-Life/blob/master/install/template_env.yml) file inside the [install](https://github.com/joaomcteixeira/Tree-of-Life/tree/master/install) folder as a guide to the required Python dependencies.

The installation process is recorded in a `install.log` file.


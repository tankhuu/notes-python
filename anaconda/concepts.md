# Concepts of Anaconda

## Commands

> conda

Query and search the Anaconda package index and current Anaconda installation.
Create new conda environments.
Install and update packages into existing conda environments.

```
# Remove unused packages and caches.
> conda clean

# Modify configuration values in .condarc. This is modeled after the git config command. Writes to the user .condarc file (/home/docs/.condarc) by default.
> conda config

# Create a new conda environment from a list of specified packages. To use the created environment, use 'conda activate envname' look in that directory first. This command requires either the -n NAME or -p PREFIX option.
> conda create

# Display information about current conda install.
> conda info

# Installs a list of packages into a specified conda environment.
> conda install
> conda install bitarray=0.8

# List linked packages in a conda environment.
> conda list

# Low-level conda package utility. (EXPERIMENTAL)
> conda package

# Remove a list of packages from a specified conda environment.
> conda remove

# Updates conda packages to the latest compatible version.
> conda search

> conda update
```

[References](https://docs.conda.io/projects/conda/en/latest/commands.html)

## Packages

A conda package is a compressed tarball file (.tar.bz2) or .conda file that contains:

- system-level libraries.
- Python or other modules.
- executable programs and other components.
- metadata under the info/ directory.
- a collection of files that are installed directly into an install prefix.

### Usage

```
conda search scipy
conda install scipy
conda build my_fun_package # build a package after installing conda-build
```

## Package Specification

## Channels

Conda channels are the locations where packages are stored. They serve as the base for hosting and managing packages. Conda packages are downloaded from remote channels, which are URLs to directories containing conda packages. The conda command searches a default set of channels, and packages are automatically downloaded and updated from https://repo.anaconda.com/pkgs/. You can modify what remote channels are automatically searched. You might want to do this to maintain a private or internal channel. For details, see how to modify your channel lists.

We use conda-forge as an example channel. Conda-forge is a community channel made up of thousands of contributors. Conda-forge itself is analogous to PyPI but with a unified, automated build infrastructure and more peer review of recipes.

## Environments

A conda environment is a directory that contains a specific collection of conda packages that you have installed. For example, you may have one environment with NumPy 1.7 and its dependencies, and another environment with NumPy 1.6 for legacy testing. If you change one environment, your other environments are not affected. You can easily activate or deactivate environments, which is how you switch between them. You can also share your environment with someone by giving them a copy of your environment.yaml file. For more information, see Managing environments.

Conda directory structure

ROOT_DIR
The directory that Anaconda or Miniconda was installed into.

## Installing with Conda

## Performance

## Conda for Data Scientists

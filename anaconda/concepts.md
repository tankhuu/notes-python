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

## Environments

## Installing with Conda

## Performance

## Conda for Data Scientists

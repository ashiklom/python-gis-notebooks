# Geopandas

Geopandas provides a pandas-like syntax for geospatial operations.

# Installation

## Windows

The easiest way to do it is to download and install the Anaconda Python distribution.

1. Download the Python 2.7 version of Anaconda from here: https://www.anaconda.com/distribution/

2. Open the "Anaconda prompt".
This is basically the same program as Windows PowerShell, but is pre-configured for ready access to everything inside conda.
Notably, it comes with Jupyter, pandas, and more pre-installed.

3. Run the command `conda install --channel conda-forge geopandas`.

## MacOS

The Anaconda instructions should work for MacOS as well.
However, I would recommend setting up [Homebrew](https://brew.sh/) instead.
Homebrew is a "package manager" for MacOS that makes it easy to install all kinds of software useful for programming, including the dependencies of geopandas.

1. Open a Terminal window and copy-paste the following command to install Homebrew.
Respond to the various prompts accordingly.

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

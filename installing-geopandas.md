# Installing Geopandas

## Windows

The easiest way to do it is via the Anaconda Python 3 distribution.
(NOTE: That installation most likely will _not_ work with Python 2).

1. Use this link to download the Python 3.7 distribution of Anaconda:
https://repo.anaconda.com/archive/Anaconda3-2019.10-Windows-x86_64.exe 

2. Run the installer you downloaded in the previous step.
The default recommended settings ("Install for just me", "Do not modify the PATH variable", "Make this the default Python") should be fine.

3. Open the Windows/Start menu (or push the Windows key), search for "Anaconda Prompt", and launch the "Anaconda Prompt (Anaconda 3)".
This is basically the same program as Windows PowerShell, but is pre-configured for ready access to everything inside Anaconda.
Notably, it comes with `jupyter`, `pandas`, `numpy`, and more pre-installed.

3. Run the command `conda install geopandas`.
After a few moments, you should be presented with a list of packages and asked if you want to install them.
Respond `Y` (yes) and wait for the packages to be installed.

## MacOS

The Anaconda instructions should work for MacOS as well.
However, I would recommend setting up [Homebrew](https://brew.sh/) instead.
Homebrew is a "package manager" for MacOS that makes it easy to install all kinds of software useful for programming, including the dependencies of geopandas.

1. Open a Terminal window and copy-paste the following command to install Homebrew.
Respond to the various prompts accordingly.

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Once Homebrew is installed, run the following command to install the system dependencies of geopandas.

   ```
   brew install gdal spatialindex
   ```
   
3. If that completes successfully, you should be able to use `pip` to install `geopandas` and two of its optional dependencies that we'll need---`descartes` for mapping and `rtree` for certain spatial operations.
From the terminal, run the following command:

   ```
   pip install --user geopandas descartes rtree
   ```

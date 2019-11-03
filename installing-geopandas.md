# Installing Geopandas

## Windows

The easiest way to do it is via the Anaconda Python 3 distribution.
(NOTE: That installation most likely will _not_ work with Python 2).

1. Use this link to download the **Python 3.7** distribution of Anaconda:
https://www.anaconda.com/distribution/

2. Run the installer you downloaded in the previous step.
The default recommended settings ("Install for just me", "Do not modify the PATH variable", "Make this the default Python") should be fine.

3. Open the Windows/Start menu (or push the Windows key), search for "Anaconda Prompt", and launch the "Anaconda Prompt (Anaconda 3)".
This is basically the same program as Windows PowerShell, but is pre-configured for ready access to everything inside Anaconda.
Notably, it comes with `jupyter`, `pandas`, `numpy`, and more pre-installed.
**From this point forward, you should use the Anaconda Prompt instead of Windows Powershell**.

3. Run the command `conda install geopandas`.
After a few moments, you should be presented with a list of packages and asked if you want to install them.
Respond `Y` (yes) and wait for the packages to be installed.

There are pretty significant differences---almost invariably for the better---between Python 2 and 3.
However, relatively few of these are user-facing, especially at the introductory level, and none of them affect the key concepts we have covered in class.
Unfortunately, few (if any) of your LPHW homework scripts will run under Python 3; that said, we're done with that book in this class, and given that Python 2 will reach the end of its official support January 1, 2020, it's better to get used to Python 3 anyway.
The main differences you will have to get used to are:

- Python 3 does not allow the `print` statement (without parentheses), only the `print()` function (which requires parentheses).
Python 2 supports both forms.
So code like this:
```python
print "hello, world!"
```
...should now be written like this:
```python
print("hello, world")
```
Code like this for printing multiple things on the same line:
```python
print "hello",
print "world"
```
...can be re-written like this:
```python
print("hello", end = " ")
print("world")
```

- In Python 3, you no longer have to worry about truncation during integer division.
So code like `7 / 5` will produce the expected `1.4`, whereas in Python 2 it would truncate to `1`.

- In Python 3, you cannot use `file()` to open files---you have to use `open()` instead.
(Python 2 supports both).
The type of the resulting object will also be different.
However, all of the remaining file operations (`read()`, `write()`, etc.) should work basically the same way.

See [here](https://python-future.org/compatible_idioms.html#essential-syntax-differences) for a more comprehensive list of syntax differences.

## MacOS

The Anaconda instructions above should work for MacOS as well.
However, I would recommend setting up [Homebrew](https://brew.sh/) instead.
Homebrew is a "package manager" for MacOS that makes it easy to install all kinds of software useful for programming, including the dependencies of `geopandas`.

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
   
## Check that the installation was successful

Open Python and check that you can run `import geopandas` without any errors.

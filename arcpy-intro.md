# Introduction to Arcpy

**Goal**: Develop a module for doing some simple spatial analysis with Arcpy.

This notebook is hosted on GitHub at https://github.com/ashiklom/python-gis-notebooks

Find Census shapefiles here: https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html

## Exercise 1: Clipping by state

### Download and extract the data

Use the "Web Interface" link and download the following shapefiles (from year 2018) into your personal `S:` drive folder:

- State boundaries
- Congressional districts

Unzip each file after downloading it (right-click and click "Extract All").

### Load the data

1. Open ArcMap and create a new blank map.
2. Add the folder where you downloaded the results to your "Folder connections".
3. Add the state and congressional district shapefiles to your map the Layers list.

### Select: Interactively

1. Open the "Analysis" toolbox.
2. Open the Analysis -> Extract -> Select tool.
3. Set the state layer (or shapefile) as your "Input feature", and use the "Expression" box to select a state by its `NAME` attribute. (Saving this to the default output location is fine).
   - Pay attention to the quoting pattern (single vs. double quotes) of the resulting syntax. The column name---in this case `"NAME"`---should be in _double_ quotes, while its target value---e.g. `'Arkansas'`---should be in single quotes.
   - The resulting expression should be `"NAME" = 'Arkansas'`
   
If successful, this should produce a new shapefile with just your selected state.

### Setup for `arcpy`

1. Open PowerShell.
2. Use `cd <path>` to navigate to the directory containing your downloaded shapefiles.
3. Start a Jupyter notebook here with the `jupyter-notebook` command.
4. Load the `arcpy` and `os` modules.

```python
import os
import arcpy
```

5. Check that you are in the right directory with:

```python
os.getcwd()
```

6. Create a new folder for storing outputs.

```python
os.mkdir("output")
```

### Select: Now with `arcpy`

To perform the same selection from above, use the following command:

```python
arcpy.Select_analysis(
    # Input feature
    "./tl_2018_us_state/tl_2018_us_state.shp",
    # Output shapefile
    "./output/select_Arkansas.shp",
    # Expression
    '"NAME" = \'Arkansas\''
)
```

### Exercise

Write a function `state_select(state)` that will perform this process for an arbitrary state and return the path to the output shapefile as a string.

```python
def select_state(state):
    # your code here...
    # 
```

### Clip: Interactively

Go back to your ArcMap window.

Use the Analysis -> Extract -> Clip tool to create a new shapefile with the congressional districts for only your selected state.
The Input Features will be the complete congressional district map.
The Clip Features ("mask") will be the selected state.

### Exercise: Clip using `arcpy`

Still in ArcMap, right-click on the "Clip" tool and open its Help page.
Scroll down to the "Syntax" and "Code sample" sections and read them.
Then, based on what you've learned:

1. Use an `arcpy` command to perform the same clip as you did above (Hint: Use the output file from your previous select statement).
2. Write a function `state_districts_116(state)` that takes the name of a state as an input and creates a shapefile.
3. Create a `list` of 3-5 states and write a `for` loop that will create shapefiles of the congressional districts from each of these states.

# Homework for this week

When you are finished with the in-class exercises, get started on your homework for this week.
Similarly to last week, your homework this week is to **find some spatial data (preferably related to your project) and use `arcpy` to do something interesting with it**.
The formal requirements here are, again, limited, but I expect you to write and use at least 2 custom Python functions that collectively perform at least 3 different GIS operations (e.g. Select, Clip, Buffer, Spatial Join).

Note that **you cannot install `arcpy` on your own laptop unless you have ArcMap** and **the only way to run `arcpy` on Citrix is through the ArcMap python window**, which is _much_ more annoying.
So it is in your best interest to make as much progress on this homework in class as you can.

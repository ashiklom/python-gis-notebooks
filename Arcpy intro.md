# Introduction to Arcpy

**Goal**: Develop a module for doing some simple spatial analysis with Arcpy.

This notebook is hosted on GitHub at https://github.com/ashiklom/python-gis-notebooks

## Step 1: Download and extract the data

Find Census shapefiles here: https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html

Use the "Web Interface" link and download the following shapefiles into your personal `S:` drive folder:

- State boundaries
- Congressional districts from year 2016

Unzip each file after downloading it (right-click and click "Extract All").

## Step 2: Interactive Python in ArcMap

### Select

Select a state interactively using the "Analysis/Extract/Select" tools.

Right click the Select tool and click "Help". Note the "Code sample" at the bottom.

Open ArcMap. Then, open the Python window.

Configure the environment by running the following commands:

(Note the `r` -- this prevents escape characters from messing up your path).

(HINT: Rather than typing it, copy-paste the path from Windows Explorer).

This tells Arcpy to use that path as the current environment.

```python
import arcpy
arcpy.env.workspace = r"<path to your environment>"
arcpy.env.overwriteOutput = True
```

Now, try to replicate the selection in Arcpy.

```python
arcpy.Select_analysis(
    "tl_2019_us_state/tl_2019_us_state.shp",
    "output/Arkansas_selected.shp",
    "\"NAME\" = 'Arkansas'"
)
```

## Step 3: Turning it into a module

In your current workspace folder, create a Python script called `spatialhelpers.py` with the following contents:

```python
import arcpy
# arcpy.env.workspace = r"path/to/workspace"

def state_name(state):
    return "\NAME\" = '%s'" % state

def select_state(state):
    input = "tl_2019_us_state/tl_2019_us_state.shp"
    output = "output/%s_selected.shp" % state
    query = state_name(state)
    arcpy.Select_analysis(input, output, query)
    return output
```

Load it in the Python window with `import spatialhelpers`.

### Clip

Now, get the congressional districts for the selected state using "Clip".

Again, look at the "Help" for the "Clip" operation, and based on that, try to reproduce it in Python.

```python
arcpy.Clip_analysis(
    "tl_2016_us_cd115/tl_2016_us_cd115.shp",
    "output/Arkansas_selected.shp",
    "output/Arkansas_districts.shp"
)
```

## Exercise

Write a function `state_districts_115(state)` that creates a shapefile of just that state's congressional districts from the 115th Congress (2016).

```python
def state_districts_115(state):
    input = "tl_2016_us_cd115/tl_2016_us_cd115.shp"
    clipby = select_state(state)
    output = "output/%s_districts_115.shp" % state
    arcpy.Clip_analysis(input, clipby, output)
    return output
```

```python

```

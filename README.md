# Metrics

Compute continuous measurements of valley floor width and valley depth from given floor polygons, river network, and dem.

Recommend to get valley floors using valleyx.

## Measurements of Valley Floor Width

Need to test the three methods for width calculation, and pick the best

1. Greg's integral of function of ratio of inner and outer area of valley from increases in radius
2. medial axis paths of valley (meaning integrates info about river network into centerlines of the valley polygon), then assign each pixel to the geodesic distance to the nearest medial axis pixel, then calculate width from the mean width for that medial axis segment perpendicular to the segment.
3. create lines around the river pixel being sample at every 10 degrees, find where those lines intersect the valley polygon, and calculate the width from the distance between the two points of intersection, get median or mean of all the generated line widths.

## Measurements of Valley Depth

doesn't need valley floors delineated, just the river network and dem
Decide between the two methods for valley depth calculation, and pick the best

1. 
    + Detect ridge pixels (flow accumulation = 0, or that matlib library that does ridge network analysis, or the ridge network from usgs valley depth module's method, or potential whiteboxtools method) 
    + for each pixel in the river network, get its catchment id, and then find the nearest ridge point for all the hillslope ids in its neighborhood and the valley depth is thus the mean of the differences between the different peak dem values and the river pixel dem value.
2. USGS valley depth module

can compare these with field measurments of valley depth and width

# Installation

1. Clone the repository

```bash
git clone git@github.com:avkoehl/valley-metrics.git
cd valley-metrics 
```

2. Install the dependencies

```bash
# Basic installation
poetry Installation

# With development dependencies (matplotlib, jupyter, etc.)
poetry install --dev
```

If planning to develop in ipykernal, install the kernel:

```bash
poetry run python -m ipykernel install --user --name=valley-metrics
```

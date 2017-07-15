# Matplotlib low level graphic elements

## Figure, Axes and Subplot

* **`Figure`** is a window or a top level container which hosts axes or any other graphic elements.
* **`Axes`** is a plotting area or a coordinate system for plotting. **`Axes`** can not exist without a **`Figure`** instance.
* **`Subplot`** is an **`Axes`** which is already bound to a **`Figure`** instance.

### Figure and Axes

The image below shows how axes instances are added to a figure instance:

![figure and axes](images/figure-and-axes.png)

### Subplot

The image below shows how to create a **`subplot`** and edit it.

![subplot](images/subplot.png)

We can easily create multiple subplots within a figure container with `subplots()`. The image below
shows how to create multiple subplots within a figure container, how to access specific subplot and edit
its attributes and how to add additional axes to a figure container which already hosts multiple subplots.

![subplots](images/subplots.png)

### Figure parameters

Below is a comparison between two figure instances with different parameter values.

![figure-parameters](images/figure-parameters.png)


## `Line2D` and `Patch`

### `Line2D`

**`Line2D`** class is used to draw a variety of line styles. Like **`Axes`** instances, **`Line2d`** instances
can be added to a figure container.

```python
import numpy as np
x1, y1 = np.random.rand(10), np.random.rand(10)
x2, y2 = np.random.rand(10), np.random.rand(10)

# figuare attributes
fig = plt.figure()

# Line2D and Patch
from matplotlib.lines import Line2D
l1 = Line2D(xdata=x1, ydata=y1, transform=fig.transFigure, figure=fig, color='red')
l2 = Line2D(xdata=x2, ydata=y2, transform=fig.transFigure, figure=fig, linestyle='-.', color='blue')

fig.lines.extend([l1, l2])
fig.canvas.draw()
```

Note that range of the width and height of the default figure container is within (0, 1). if
your x, y values is outside this range, you won't be able to see the points on the figure.

<p align="center"><img src="images/line2d-on-figure.png" width=600></p>

### `Patch`

The **`Patch`** class is used draw plane-like artists. The `facecolor` and `edgecolor` are two common
properties of a **`Patch`** instance. Like `Axes` and `Line2D`, we can add `Patches` directly to the `figure` container.

```python
import matplotlib.path as mpath
import matplotlib.patches as mpatches

cp = mpatches.CirclePolygon(xy=(200, 200), radius=50)
el = mpatches.Ellipse(xy=(350, 300), width=210, height=100, angle=45, color="green")

fig = plt.figure()
fig.patches.extend([cp, el])
fig.canvas.draw()
```

<p align="center"><img src="images/patch-on-figure.png" width=600></p>





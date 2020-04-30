# **PYTHON: MATPLOTLIB**

Matplotlib is a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms. Developer can generate plots, histograms, power spectra, bar charts, error charts, scatterplots, and more with just a few lines of code.

To install Matplotlib library, open command prompt window and enter the command below: 

```
python -m pip install matplotlib
```

Since Matplotlib is a huge scientific library and is still growing, this chapter will briefly introduce basic terminology and its mechanism. For more information, refer to the following URL: https://matplotlib.org/

## Terminology

Matplotlib has various term user and developer may not be familiar of. This section is hereby provide terminology used in the library that could help understand. Below is a figure from official Matplotlib website:

<div style="background:white; border:solid 3px #808e95; text-align: center; border-radius:0.5em; padding:0.5em 0 0.5em 0;"><img src=".\.images\Python\matplotlib_terminology.png" width=100%></div><center style="font-weight:bold">Figure #. Matplotlib terminology.</center>
### Figure

Figure is considered an empty window of easel (a standing frame for a canvas):

<div style="background:white; border:solid 3px #808e95; text-align: center; border-radius:0.5em; padding:0.5em 0 0.5em 0;"><img src=".\.images\Python\matplotlib_figure_no_axes.png" width=70%></div><center style="font-weight:bold">Figure #. Matplotlib figure without any axes.</center>
Calling a figure using API such as `matplotlib.pyplot.figure()` returns pure white window background without anything.

### Axes

Axes (aka. subplot) is the region of the image with the data space, considered as canvas that goes up on easel. Do not be confused with axes and axis which is completely different. A following is a figure with four empty axes:

<div style="background:white; border:solid 3px #808e95; text-align: center; border-radius:0.5em; padding:0.5em 0 0.5em 0;"><img src=".\.images\Python\matplotlib_figure_with_axes.png" width=70%></div><center style="font-weight:bold">Figure #. Matplotlib figure with four axes.</center>
API such as `matplotlib.pyplot.subplot()` or `matplotlib.pyplot.subplots()` returns both figure and a single or multiple empty axes simultaneously.
---
title: "Introduction to pandas"
teaching: 5
exercises: 0
questions:
- "What is pandas?"
objectives:
- "Short introduction to pandas"
keypoints:
- "Pandas makes tabular data analysis simple"
---

## The `pandas` library


The `pandas` library was created by [Wes McKinney](http://wesmckinney.com/) in 2011. `pandas` provides **data structures** and **functions** 
for manipulating, processing, cleaning and crunching data. In the Python ecosystem `pandas` is the state-of-the-art tool for working with tabular or spreadsheet-like data  in which each column may be a different type (`string`, `numeric`, `date`, or otherwise). `pandas` provides sophisticated indexing functionality to make it easy to reshape, slice and dice, perform aggregations, and select subsets of data. 
 
`pandas` relies on other packages, such as `NumPy`, short for *Numerical Python*, one of the foundational packages of scientific computing with Python and `SciPy`, a collection of packages addressing a number of different standard problem domains in scientific computing. 
Further `pandas` integrates `matplotlib`, probable the most popular Python library for plotting and 2D data visualizations. 


Once installed (for details refer to the [documentation](https://pandas.pydata.org/pandas-docs/stable/install.html)), we import the `pandas` library into your Python session by using the canonical alias `pd`.

~~~
import pandas as pd
~~~
{: .language-python}

The pandas library has two workhorse data structures: __*Series*__ and __*DataFrame*__.

***

---
title: "The pandas Series"
teaching: 20
exercises: 5
questions:
- "What is a pandas Series?"
- "How to use the pandas API?"
objectives:
- "Learn how to use pandas for exploring and analyzing one-dimensional data sets."
keypoints:
- "Pandas rulez!"
---


The pandas library has two workhorse data structures: __*Series*__ and __*DataFrame*__.

***

## `pd.Series` object 

A Series is a one-dimensional array-like object containing an array of data and an associated array of data labels, called its _index_. We create a `pd.Series` object by calling the `pd.Series()` function. 


> ## Functions and their arguments
>
> Look up the documentation for a function to learn more about its general usage, its input arguments and its return value(s). In IPython we use the `?` or `??` magic commands to look up the documentation.    
>
> ~~~
> ?pd.Series
> # or
> ??pd.Series
> ~~~
>
> If you done it right, a pop-up window appears with many useful information on the particular function call.
> {: .language-python}
{: .callout}


The `pd.Series` function call is structured as follows:

~~~
pd.Series(data=None, index=None, dtype=None, name=None, copy=False, fastpath=False)
~~~ 
{: .output}

For the sake of this tutorial we generate random data using `numpy`.

~~~
# import the random module from numpy
from numpy import random 
# set seed for reproducibility
random.seed(123) 
# generate 26 random integers between -10 and 10
my_data = random.randint(low=-10, high=10, size=26)
# print the data
my_data
~~~
{: .language-python}

~~~
array([  3,  -8,  -8,  -4,   7,   9,   0,  -9, -10,   7,   5,  -1, -10,
         4, -10,   5,   9,   4,  -6, -10,   6,  -6,   7,  -7,  -8,  -3])
~~~
{: .output}

Once we have the data, we create a `pd.Series` object and store it in the variable `s`. 


> ## Default values of function arguments
>
> Most functions provide default values for most of their input arguments. 
> Note that we do not provide an `index` argument in the function call below, hence `pandas` will generate a zero-based integer index automatically. (Nor we provid an argument for `dtype`, `name`, `copy`,  and `fastpath`; we stay with the defaults) 
{: .callout}


~~~
# create a pd.Series object
s = pd.Series(data=my_data)
~~~
{: .language-python}


Let us inspect the variable `s`.


~~~
s
~~~
{: .language-python}

~~~
0      3
1     -8
2     -8
3     -4
4      7
5      9
6      0
7     -9
8    -10
9      7
10     5
11    -1
12   -10
13     4
14   -10
15     5
16     9
17     4
18    -6
19   -10
20     6
21    -6
22     7
23    -7
24    -8
25    -3
dtype: int32
~~~
{: .output}

We see the one-dimensional array-like object nicely formatted. Note the last line of the output: `dtype: int32`. This indicates that we store 32-bit integer values in our Series object.

We can check the object type by typing `type(OBJECT)` into our console.

~~~
type(s)
~~~
{: .language-python}

~~~
pandas.core.series.Series
~~~
{: .output}

Perfect!



***
### `pd.Series` attributes

Python objects in general and the `pd.Series` in particular offer useful object-specific *attributes*.


> ## Attributes
>
> Attributes are accessed using the attribute notation.  Hence we simply appending a dot (`.`) to the Python object. 
>~~~
>OBJECT.attribute_name
>~~~
>{: .language-python}
{: .callout}

Several attributes are defined for a `pd.Series` object, such as the `dtypes` attribute,

~~~
s.dtypes
~~~
{: .language-python}

~~~
dtype('int32')
~~~
{: .output}


and the `index` attribute.

~~~
s.index
~~~
{: .language-python}

~~~
RangeIndex(start=0, stop=26, step=1)
~~~
{: .output}


Note that there are more attributes, which some of them will be discussed in the subsequent sections, others are discussed elsewhere.  


> ## Reassigning the index of a `pd.Series` object.
>Change the index to of the `pd.Series` object `s` to upper-case letters of the alphabet.   
{: .challenge}

>## Hint 1
>In order to get you started we use the `string` model to generate a `string` object with all upper-case letters of the alphabet.
>~~~
>import string
>letters = string.ascii_uppercase
>letters
>~~~
>{: .language-python}
>~~~
>'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
>~~~
>{: .output}
{: .solution}

>## Hint 2
>
>Note that in Python a `string` object is an iterable. Hence we may use a list comprehension to get an array-like representation of a `string` object.
>~~~
>[x for x in STRING]
>~~~
>{: .language-python}
{: .solution}


>## Hint 3
>
>`pandas` provides several methods for assignsin an _index_ to a `ps.Series`. Probably the most intuitive way is to reassign the `pd.Series.index` attribute.
>~~~
>mySeries.index = new_index
>~~~
>{: .language-python}
{: .solution}



> ## Solution
>
>~~~
>import string
>letters = string.ascii_uppercase
>s.index = [l for l in letters]
>s
>~~~
>{: .language-python}
>~~~
>A     3
B    -8
C    -8
D    -4
E     7
F     9
G     0
H    -9
I   -10
J     7
K     5
L    -1
M   -10
N     4
O   -10
P     5
Q     9
R     4
S    -6
T   -10
U     6
V    -6
W     7
X    -7
Y    -8
Z    -3
dtype: int32
>~~~
>{: .output}
{: .solution}

Call `s.index` once more an print the variable `s` to the screen to make sure it worked out as expected.

~~~
s.index
~~~
{: .language-python}

~~~
Index(['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'], dtype='object')
~~~
{: .output}


~~~
s
~~~
{: .language-python}

~~~
A     3
B    -8
C    -8
D    -4
E     7
F     9
G     0
H    -9
I   -10
J     7
K     5
L    -1
M   -10
N     4
O   -10
P     5
Q     9
R     4
S    -6
T   -10
U     6
V    -6
W     7
X    -7
Y    -8
Z    -3
dtype: int32
~~~
{: .output}



***
### `pd.Series` methods

Python objects in general and the `pd.Series` in particular offer useful object-specific *methods*.

   
> ## Methods
>
> Methods are functions that are called using the attribute notation.  Hence they are called by appending a dot (`.`) to the Python object, followed by the name of the method, parentheses `()` and in case one or more arguments (`arg`). 
>~~~
>OBJECT.method_name(arg1, agr2, ...)
>~~~
>{: .language-python}
{: .callout}

Several methods are defined for a `pd.Series` object, such as the `sum()` method,

~~~
s.sum()
~~~
{: .language-python}

~~~
-34
~~~
{: .output}


the `mean()` method,

~~~
s.mean()
~~~
{: .language-python}

~~~
-1.3076923076923077
~~~
{: .output}


the `max()` method,

~~~
s.max()
~~~
{: .language-python}

~~~
9
~~~
{: .output}


the `min()` method,

~~~
s.min()
~~~
{: .language-python}

~~~
-10
~~~
{: .output}


the `median()` method,

~~~
s.median()
~~~
{: .language-python}

~~~
-2.0
~~~
{: .output}


which is mathematically equivalent to the `quantile(q=0.5)`.

~~~
s.quantile(q=0.5)
~~~
{: .language-python}

~~~
-2.0
~~~
{: .output}


The `quantile()` method is even more versatile, as we can specify more then one quantile. All we have to do is to provide a Python list object to the method call.

~~~
s.quantile(q=[0.25, 0.5, 0.75])
~~~
{: .language-python}

~~~
0.25   -8.0
0.50   -2.0
0.75    5.0
dtype: float64
~~~
{: .output}


Note that there are many more methods, which some of them will be discussed in the subsequent sections, others are discussed elsewhere.  




***

### Element-wise arithmetic

A very useful feature of `pd.Series` objects is that we may apply arithmetic operations *element-wise*. 

Consider our Series object `s`. For example, if we want to multiply each element by 0.1, we may simply write

~~~
s*0.1
~~~
{: .language-python}

and get as results

~~~
0     0.3
1    -0.8
2    -0.8
3    -0.4
4     0.7
5     0.9
6     0.0
7    -0.9
8    -1.0
9     0.7
10    0.5
11   -0.1
12   -1.0
13    0.4
14   -1.0
15    0.5
16    0.9
17    0.4
18   -0.6
19   -1.0
20    0.6
21   -0.6
22    0.7
23   -0.7
24   -0.8
25   -0.3
dtype: float64
~~~
{: .output}

Note that the `dtype` of the resulting Series is automatically set to `dtype: float64`.

> ## Element-wise arithmetic with `pd.Series` objects?
>
>Try it by your own and conduct some arithmetic calculations with the `pd.Series` object `s`.
{: .challenge}

> ## Hint
> Try out the following:
>~~~
>s+10
>10/s
> s**2
>(2+s)*1**3
># we are sure you you got it by now ;-) 
>~~~
>{: .language-python}
{: .solution}

### Selection and Indexing 

Another main data operation is indexing and selecting particular subsets of the data object. `pandas` comes with a very [rich set of methods](https://pandas.pydata.org/pandas-docs/stable/indexing.html) for these type of tasks.  

In its simplest form we index a Series `numpy`-like, by using the `[]` operator to select a particular `index` of the Series.

In order to index the fourth element (be aware that in Python we start counting with 0!!) of the `pd.Series` object, `s`, we write

~~~
s[3]
~~~
{: .language-python}
~~~
-4
~~~
{: .output}

Note that pandas returns a numeric value.

Further, we may select a slice of the Series in form of `[start:end]`. We select a slice, ranging from the third to the sixth element by typing 

~~~
s[2:6]
~~~
{: .language-python}
~~~
2   -8
3   -4
4    7
5    9
dtype: int32
~~~
{: .output}

Once again note that the third to the sixth element of the Series occur at the index position two to five. Further note that this time `pandas` returns a `pd.Series` object.


In addition to the `[]` operator `pandas` ships with other indexing operators such as `.loc[]` and `.iloc[]`, among others. We learn more about these types of operators in the subsequent sections, when we are dealing with `pd.DataFrame` objects. But please note that those operators work equivalently on `pd.Series` objects. 

***

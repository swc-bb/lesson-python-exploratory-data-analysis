---
title: "The pandas DataFrame"
teaching: 20
exercises: 15
questions:
- "What is a pandas DataFrame?"
- "How to use the pandas API?"
objectives:
- "Learn how to use pandas for exploring and analyzing spreadsheet like data sets."
keypoints:
- "Pandas rulez!"
---

The pandas library has two workhorse data structures: __*Series*__ and __*DataFrame*__.

***

## `pd.DataFrame` object


The primary object in pandas that will be used in this book is the DataFrame, a two-dimensional
tabular, column-oriented data structure with both row and column labels:

***

### `pd.DataFrame` attributes



***

### `pd.DataFrame` methods




**`groupby` method**

Split-apply-combine paradigm

**`plot` method**

***

### Selection and Indexing


* `.loc[]` is primarily **label based**, but may also be used with a boolean array. `.loc[]` will raise `KeyError` when the items are not found.   
* `iloc[]` is primarily **integer position based** (from 0 to length-1 of the axis), but may also be used with a boolean array. `iloc[]` will raise `IndexError` if a requested indexer is out-of-bounds.



**The column index**

**The row index**

**Row and columns indices**

***
### Manipulating columns, rows and particular entries

**Add a row to the data set**

**Add a column to the data set**

**Change a particular entry**





> ## Inclusive vs. exclusive upper-bounds?
>
> Note that with respect to indexing `pandas` is different form many other libraries in Python ecosystem such as `numpy` or the standard library. Is to say, in `pandas`, if we type `[0:1]` we get in return two items, **the first and the second item** (=*inclusive*). 
However, if we index an `numpy.array` object or a `list` object with `[0:1]` **only the first item** is returned (=*exclusive*)! 
Consider the following example:   
>~~~
> # generate a list of integers, 1 to 4, using the range function
>l = list(range(1,5)) # exclusive
>l
>~~~
>{: .language-python}
>~~~
>[1, 2, 3, 4]
>~~~
>{: .output}
>~~~
> # selecting the first TWO elements of the list
>l[0:2] # exclusive
>~~~
>{: .language-python}
>~~~
>[1,2]
>~~~
>{: .output}
> ~~~
># the pandas way 
>ss = pd.Series(l) 
>ss[0:2] #exclusive
>~~~
>{: .language-python}
>~~~
>0    1
>1    2
>dtype: int64
>~~~
>{: .output}
> ~~~
># the pandas way 
>ss = pd.Series(l) 
># .iloc
>s.iloc[0:2] #exclusive
>~~~
>{: .language-python}
>~~~
>0    1
>1    2
>dtype: int64
>~~~
>{: .output}
>~~~
># .loc
>s.loc[0:2] #inclusive
>~~~
>{: .language-python}
>~~~
>0    1
>1    2
>2    3
>dtype: int64
>~~~
>{: .output}
{: .callout}

***
[Pandas](http://pandas.pydata.org/pandas-docs/stable/) is a Python module that allows for easy and quick manipulation of [data frames](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html). One of the most convient aspects of Pandas is that it allows for indexing by both text and numeric index labels.

We can first initialize a dataframe with two columns, A and B. The `.head()` command shows the top five rows of a data frame, viewing df shows us our table with column indices A and B and row indices 0 and 1. 
```python
In [1]: import pandas as pd

In [2]: df = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})

In [3]: df.head()
Out[3]:
   A  B
0  1  3
1  2  4
```

Labeled indices can be accessed through the command `.loc[row index, column index]` and integer index can be accessed through the `.iloc[row index, column index]`. `:` can be used to specify all values along the specified axis. For example,
```python
In [4]: df.loc[0, 'A']
Out[4]: 1

In [5]: df.iloc[0,0]
Out[5]: 1

In [6]: df.loc[:, 'A']
Out[6]:
0    1
1    2
Name: A, dtype: int64
```

The above example is a familiar one, text labeled columns and numeric labeled rows. Let's consider an example with text labels for both rows and columns,
```python
In [7]: df = pd.DataFrame({'A': [1,2], 'B': [3,4]}, index = ['zero', 'one']); df.head()
Out[7]:
      A  B
zero  1  3
one   2  4

In [8]: df.loc['zero', 'A']
Out[8]: 1

In [9]: df.loc[0, 'A']
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
```

Oops! We mixed label types. In the first example, the rows were labeled with integers and thus `loc` and `iloc` will treat the rows the same. Even with both rows and columns having text labels, `iloc` can be used to access the first element,
```python
In [10]: df.iloc[0,0]
Out[10]: 1
```

Read more from the [official documentation](http://pandas.pydata.org/pandas-docs/stable/indexing.html) and the [official tutorials](https://pandas.pydata.org/pandas-docs/stable/tutorials.html).

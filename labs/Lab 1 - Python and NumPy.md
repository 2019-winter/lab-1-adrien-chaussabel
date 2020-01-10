---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**Adrien Chaussabel**



**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**





1. 
2.
3.


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = np.full((6, 4), 2)
a
```

## Exercise 2

```python
b = np.full((6, 4), 1)
np.fill_diagonal(b, 3)
b
```

## Exercise 3

```python
print(a * b) # works because the dimensions are same
print(np.dot(a, b)) # does not work because the number of columns in a does not equal the number of rows in b
```

## Exercise 4

```python
print(np.dot(a.transpose(), b)) # works because now the number of columns of a is 4, and number of rows in b is 4
print()
print(np.dot(a, b.transpose())) # does not work because number of columns of a is 6, and number of rows in b is 6
```

## Exercise 5

```python
def print_something():
    print("something")

print_something()
```

## Exercise 6

```python
def print_stats():
    row = np.random.randint(1, 10)
    col = np.random.randint(1, 10)
    matr = np.random.randint(0, 100, size=(row, col))
    print(matr)
    print("Mean =", np.mean(matr))
    print("Std Dev =", np.std(matr))
    print("Min =", np.min(matr))
    print("Max =", np.max(matr))
    print("Sum =", np.sum(matr))

print_stats()
```

## Exercise 7

```python
def countOnesLoop(matr):
    cnt = 0
    for i in matr:
        if i == 1:
            cnt += 1
    return cnt

def countOnesWithWhere(matr):
    return np.where(matr == 1, 1, 0).sum()

print(countOnesLoop(np.array([1,2,3,4,5,1])))
print(countOnesWithWhere(np.array([1,2,3,1,4,5,1])))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# 2 Methods to convert
import pandas as pd

df1 = pd.DataFrame(2, index = range(6), columns = range(4))
print(df1)
print("\nOr..\n")
df2 = pd.DataFrame(np.full((6, 4), 2))
print(df2)

```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b2 = pd.DataFrame(1, index = range(6), columns = range(4))

np.fill_diagonal(b2.values, 3)
b2
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# cross
print(df1.multiply(b))
# dot
df1.dot(b) # doesn't work because product shape is mismatched
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def countOnesPD(df):
    cnt = 0
    for i in range(df.shape[0]):
        for j in range(df.shape[1]):
            if df.iloc[i, j] == 1:
                cnt += 1
    return cnt

countOnesPD(b2)
```

```python
def countByWhere(df):
    return len(np.where(df==1)[0])
countByWhere(b2)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df.iloc[:, 2:3]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)

```

```python
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
titanic_df.reset_index()
```

```python

```

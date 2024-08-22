# Column names

Polars and PyArrow only allow for string column names. What about pandas?

```python
>>> import pandas as pd
>>> pd.concat([pd.Series([1, 2], name=0), pd.Series([1, 3], name=0)], axis=1)
   0  0
0  1  1
1  2  3
```

Oh...not only does it let us create a dataframe with a column named `0` - it lets us
create one with _two_ such columns!

What does Narwhals do about this?

- In general, non-string column names are supported. In some places where this might
  create ambiguity (such as `DataFrame.__getitem__`) we may be strict and only
  allow passing in column names if they're strings.
- If you have a use-case that's
  failing for non-string column names, please report it to [https://github.com/narwhals-dev/narwhals/issues](https://github.com/narwhals-dev/narwhals/issues)
  and we'll see if we can support it.
- Duplicate column names are 🚫 banned 🚫.
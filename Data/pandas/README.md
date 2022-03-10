# pandas
[pandas - Python Data Analysis Library](https://pandas.pydata.org/)  
pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool.  
[pandas-dev/pandas](https://github.com/pandas-dev/pandas)

《Python for Data Analysis》

## Data structures
- Series  
  index + values
- DataFrame  
  The DataFrame has both a row and column index; it can be thought of as a dict of Series all sharing the same index.  
  对 Jupyter 有 HTML 显示
- Index Objects  
  immutable  
  label 可以重复，选取时会选取 label 对应的所有行。

就感觉到非常的灵活

## General functions
[General functions --- pandas 1.4.1 documentation](https://pandas.pydata.org/docs/reference/general_functions.html)
- Data manipulations
  - [cut](https://pandas.pydata.org/docs/reference/api/pandas.cut.html)
    ```python
    pd.cut(df['Age'][df['Survived'] == 1], bins=range(0, 101, 10), right=False).value_counts(sort=False)
    ```

## Series
[Series --- pandas 1.4.1 documentation](https://pandas.pydata.org/docs/reference/series.html)

## DataFrame
[DataFrame --- pandas 1.4.1 documentation](https://pandas.pydata.org/docs/reference/frame.html)
- Indexing, iteration

  ![](images/README/df-index.png)  
  ![](images/README/df-index2.png)

  `Series[]` 选取列，或通过 bool 数组选取行  
  `Series.loc[]` 选取行，或通过 bool 数组选取列，或同时选取行列
  - `obj[obj > 0]` 的实现是先通过 `[obj > 0]` 生成 bool Series list，再应用到 `obj` 上
  - slice 包括 end-point

  - 用 `[]` 选取多列是 `DataFrame`，选取一列是 `Series`，那么如何选取一列为 `DataFrame`？  
    `df[[col]]`
  - 如何输出某列中的所有值？  
    `.values`

- Reindexing / selection / label manipulation
  - [reindex()](https://pandas.pydata.org/docs/reference/api/pandas.Series.reindex.html)  
    Conform Series to new index with optional filling logic.  
    method: { None, 'backfill'/'bfill', 'pad'/'ffill', 'nearest' }

- Binary operator functions

  ![](images/README/df-binary.png)

- Computations / descriptive stats

  ![](images/README/df-comp.png)

  ![](images/README/df-comp2.png)

- Missing data handling
  - [replace()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.replace.html#pandas.DataFrame.replace)  
    `df.replace(0, np.nan, inplace=True)  # 0 -> np.nan`
  - isna() / isnull()  
    notna() / notnull()

- Conversion
  - [astype()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html)
  - [`pandas.to_numeric()`](https://pandas.pydata.org/docs/reference/api/pandas.to_numeric.html)

- Combining / comparing / joining / merging
  - [append()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.append.html#pandas.DataFrame.append)  (Deprecated)  
    注意，append 不会修改原 DataFrame，而是会返回新 DataFrame，与 Python 标准库行为不一致。

## Index objects
[Index objects --- pandas 1.4.1 documentation](https://pandas.pydata.org/docs/reference/indexing.html)

![](images/README/index.png)

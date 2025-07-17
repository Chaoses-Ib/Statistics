# [Polars](https://pola.rs/)
[Wikipedia](https://en.wikipedia.org/wiki/Polars_(software)), [GitHub](https://github.com/pola-rs/polars/)

- Arrow
- Rust
- Bindings: Python, Node.js, R, SQL
- Good docs

[Getting started - Polars user guide](https://docs.pola.rs/user-guide/getting-started/)

[Ecosystem - Polars user guide](https://docs.pola.rs/user-guide/ecosystem/)

[Polars: A High-Performance DataFrame Library for Rust | Ryuru](https://ryuru.com/polars-a-high-performance-dataframe-library-for-rust/) ([r/rust](https://www.reddit.com/r/rust/comments/1lxjsx9/polars_a_highperformance_dataframe_library_for/))

[pola-rs/polars-benchmark](https://github.com/pola-rs/polars-benchmark)

[Benchmark: DuckDB, Polars, Pandas, Arrow, SQLite, NanoCube on filtering / point queryies : r/Python](https://www.reddit.com/r/Python/comments/1gyoi7n/benchmark_duckdb_polars_pandas_arrow_sqlite/)

[Python Polars 1.0 is released : r/rust](https://www.reddit.com/r/rust/comments/1dsqb90/python_polars_10_is_released/)

## vs. pandas
[Coming from Pandas - Polars user guide](https://docs.pola.rs/user-guide/migration/pandas/)

[Polars vs Pandas : r/Python](https://www.reddit.com/r/Python/comments/1jg402b/polars_vs_pandas/)

[I wrote on post on why you should start using polars in 2025 based on personal experiences : r/Python](https://www.reddit.com/r/Python/comments/1jqntn9/i_wrote_on_post_on_why_you_should_start_using/)

## Python
[Installation - Polars user guide](https://docs.pola.rs/user-guide/installation/#feature-flags)

`uv add polars` (33.5 MiB)

```python
import polars as pl
```
```python
>>> df = pl.DataFrame(
...     {
...         "A": [1, 2, 3, 4, 5],
...         "fruits": ["banana", "banana", "apple", "apple", "banana"],
...         "B": [5, 4, 3, 2, 1],
...         "cars": ["beetle", "audi", "beetle", "beetle", "beetle"],
...     }
... )

# embarrassingly parallel execution & very expressive query language
>>> df.sort("fruits").select(
...     "fruits",
...     "cars",
...     pl.lit("fruits").alias("literal_string_fruits"),
...     pl.col("B").filter(pl.col("cars") == "beetle").sum(),
...     pl.col("A").filter(pl.col("B") > 2).sum().over("cars").alias("sum_A_by_cars"),
...     pl.col("A").sum().over("fruits").alias("sum_A_by_fruits"),
...     pl.col("A").reverse().over("fruits").alias("rev_A_by_fruits"),
...     pl.col("A").sort_by("B").over("fruits").alias("sort_A_by_B_by_fruits"),
... )
shape: (5, 8)
┌──────────┬──────────┬──────────────┬─────┬─────────────┬─────────────┬─────────────┬─────────────┐
│ fruits   ┆ cars     ┆ literal_stri ┆ B   ┆ sum_A_by_ca ┆ sum_A_by_fr ┆ rev_A_by_fr ┆ sort_A_by_B │
│ ---      ┆ ---      ┆ ng_fruits    ┆ --- ┆ rs          ┆ uits        ┆ uits        ┆ _by_fruits  │
│ str      ┆ str      ┆ ---          ┆ i64 ┆ ---         ┆ ---         ┆ ---         ┆ ---         │
│          ┆          ┆ str          ┆     ┆ i64         ┆ i64         ┆ i64         ┆ i64         │
╞══════════╪══════════╪══════════════╪═════╪═════════════╪═════════════╪═════════════╪═════════════╡
│ "apple"  ┆ "beetle" ┆ "fruits"     ┆ 11  ┆ 4           ┆ 7           ┆ 4           ┆ 4           │
│ "apple"  ┆ "beetle" ┆ "fruits"     ┆ 11  ┆ 4           ┆ 7           ┆ 3           ┆ 3           │
│ "banana" ┆ "beetle" ┆ "fruits"     ┆ 11  ┆ 4           ┆ 8           ┆ 5           ┆ 5           │
│ "banana" ┆ "audi"   ┆ "fruits"     ┆ 11  ┆ 2           ┆ 8           ┆ 2           ┆ 2           │
│ "banana" ┆ "beetle" ┆ "fruits"     ┆ 11  ┆ 4           ┆ 8           ┆ 1           ┆ 1           │
└──────────┴──────────┴──────────────┴─────┴─────────────┴─────────────┴─────────────┴─────────────┘
```

## [Expressions and contexts](https://docs.pola.rs/user-guide/concepts/expressions-and-contexts/)
[Expressions - Polars user guide](https://docs.pola.rs/user-guide/expressions/)

[Conditionals](https://docs.pola.rs/user-guide/expressions/basic-operations/#conditionals)

Plugins:
- [abstractqqq/polars\_ds\_extension: Polars extension for general data science use cases](https://github.com/abstractqqq/polars_ds_extension)
- [ion-elgreco/polars-distance: Polars plugin for pairwise distance functions](https://github.com/ion-elgreco/polars-distance)
- [ion-elgreco/polars-hash: Polars plugin for stable hashing functionality](https://github.com/ion-elgreco/polars-hash)

Contexts:
- `select`
- `with_columns`

  > The context `with_columns` is very similar to the context `select`. The main difference between the two is that the context `with_columns` creates a new dataframe that contains the columns from the original dataframe and the new columns according to its input expressions, whereas the context `select` only includes the columns selected by its input expressions.
- `filter`
- `group_by` and `agg`

### [Expression expansion](https://docs.pola.rs/user-guide/expressions/expression-expansion/)
> Expression expansion is like a shorthand notation for when you want to apply the same transformation to multiple columns.
```python
pl.col("weight", "height").mean().name.prefix("avg_") ==
[
    pl.col("weight").mean().alias("avg_weight"),
    pl.col("height").mean().alias("avg_height"),
]
```

## [Data types](https://docs.pola.rs/user-guide/concepts/data-types-and-structures/)
### [Structs](https://docs.pola.rs/user-guide/expressions/structs/)
Why struct fileds are not printed but only the column count?

- Flatten: [`unnest("struct_col")`](https://docs.pola.rs/api/python/stable/reference/dataframe/api/polars.DataFrame.unnest.html)
  - Not recursive
  - Why not just `flatten()`?

#### [JSON](https://docs.pola.rs/user-guide/io/json/)
[`polars.read_json` --- Polars documentation](https://docs.pola.rs/api/python/stable/reference/api/polars.read_json.html)

Supports newline-delimited JSON.

### Date times
- [pola-rs/polars-xdt: Polars plugin offering eXtra stuff for DateTimes](https://github.com/pola-rs/polars-xdt)

## [IO](https://docs.pola.rs/user-guide/io/)
[IO Plugins - Polars user guide](https://docs.pola.rs/user-guide/plugins/io_plugins/)

### [Databases](https://docs.pola.rs/user-guide/io/database/)
- [ConnectorX: Fastest library to load data from DB to DataFrames in Rust and Python](https://github.com/sfu-db/connector-x)
  - `uv add polars[connectorx,pyarrow]` (31.4+24.4 MiB)
  - SQLite: `sqlite://{path}`
- [ADBC: Arrow Database Connectivity --- Apache Arrow v20.0.0](https://arrow.apache.org/docs/format/ADBC.html)

## [Plugins](https://docs.pola.rs/user-guide/plugins/)
[pola-rs/pyo3-polars: Plugins/extension for Polars](https://github.com/pola-rs/pyo3-polars)

## [Visualization](https://docs.pola.rs/user-guide/misc/visualization/)
- [alceal/plotlars: Plotlars is a Rust library designed to facilitate the integration between the Polars data analysis library and Plotly library.](https://github.com/alceal/plotlars)

  [Title: Announcing Plotlars: Simplify Your Data Visualization Workflow in Rust! 🦀📊 : r/rust](https://www.reddit.com/r/rust/comments/1f0v0ul/title_announcing_plotlars_simplify_your_data/)

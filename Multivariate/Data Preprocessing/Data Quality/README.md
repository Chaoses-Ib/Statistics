# Data Quality
Data mining algorithms are often applied to data that was collected for another purpose, or for future, but unspecified applications. For that reason, data mining cannot usually take advantage of the significant benefits of “addressing quality issues at the source.” In contrast, much of statistics deals with the design of experiments or surveys that achieve a prespecified level of data quality.

Because preventing data quality problems is typically not an option, data mining focuses on:
- the detection and correction of data quality problems, that is, *data cleaning*
- the use of algorithms that can tolerate poor data quality, i.e., *robust algorithms.*

## Measurement errors
The term measurement error refers to any problem resulting from the measurement process.
- Noise and artifacts
  
  Noise is the random component of a measurement error.
  Data errors can be the result of a more deterministic phenomenon, such as a streak in the same place on a set of photographs. Such deterministic distortions of the data are often referred to as artifacts.
- Precision
  
  The closeness of repeated measurements (of the same quantity) to one another. Precision is often measured by the standard deviation of a set of values.
- Bias
  
  A systematic variation of measurements from the quantity being measured. Bias is measured by taking the difference between the mean of the set of values and the known value of the quantity being measured.
- Accuracy
  
  The closeness of measurements to the true value of the quantity being measured. Accuracy depends on precision and bias, but there is no specific formula for accuracy in terms of these two quantities.
  One important aspect of accuracy is the use of *significant digits*. The goal is to use only as many digits to represent the result of a measurement or calculation as are justified by the precision of the data.

## Data collection errors
The term data collection error refers to errors such as omitting data objects or attribute values, or inappropriately including a data object.

- Outliers (or anomalous objects)
  
  Outliers are either (1) data objects that, in some sense, have characteristics that are different from most of the other data objects in the data set, or (2) values of an attribute that are unusual with respect to the typical values for that attribute.
- [Missing values](Missing%20Values.md)
  
  Several strategies for dealing with missing data:
  - Eliminate data objects or attributes
  - Estimate missing values
  - Ignore the missing value during analysis
  
    Many data mining approaches can be modified to ignore missing values.
- Inconsistent values
  
  Once an inconsistency has been detected, it is possible to correct the data if additional or redundant information is available.
- Duplicate data
  
  dedeuplication

## Issues related to applications
- Timeliness
  
  Some data starts to age as soon as it has been collected.
- Relevance
  
  The available data must contain the information necessary for the application.

  A common problem is *sampling bias*, which occurs when a sample does not contain different types of objects in proportion to their actual occurrence in the population.
- Knowledge about the data
  
  Ideally, data sets are accompanied by documentation that describes different aspects of the data; the quality of this documentation can either aid or hinder the subsequent analysis.

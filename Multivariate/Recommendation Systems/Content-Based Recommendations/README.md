# Content-Based Recommendations
## Item Profiles
An **item profile** is a record (vector) or collection of records representing important characteristics of an item.

## User Profiles
A **user profile** is a vector with the same components as item profiles that describe the user's preferences.

怎么构造 user profile？首先要获得 user 评价过的 items，将 ratings 减去均值，以 ratings 为权重，计算每个 component 的平均 rating，从而得到 user profile。

## Recommending Items to Users
- Similarity between item profiles and user profiles
- Classification algorithms
  
  Item profiles + utility matrices → ratings

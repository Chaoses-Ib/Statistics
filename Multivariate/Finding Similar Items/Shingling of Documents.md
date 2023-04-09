# Shingling of Documents
## $k$-Shingles
A document is a string of characters. Define a $k$-shingle for a document to be any substring of length $k$ found within the document.

How large $k$ should be depends on how long typical documents are and how large the set of typical characters is. $k$ should be picked large enough that the probability of any given shingle appearing in any given document is low.

为什么不按单词分词？shingle 不是很容易截到无意义片段吗？
> We should understand that the aspect of similarity we are looking at here is character-level similarity, not “similar meaning,” which requires us to examine the words in the documents and their uses.

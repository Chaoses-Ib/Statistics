# Hubs and Authorities
This hubs-and-authorities algorithm, sometimes called **HITS** (hyperlink-induced topic search), was originally intended not as a preprocessing step before handling search queries, as PageRank is, but as a step to be done along with the processing of a search query, to rank only the responses to that query.

While PageRank assumes a one-dimensional notion of importance for pages, HITS views important pages as having two ﬂavors of importance:
- **Authorities**: Certain pages that are valuable because they provide information about a topic
- **Hubs**: Other pages that are valuable because they tell you where to go to find out about that topic, bot because they provide information about any topic.

Just as PageRank uses the recursive deﬁnition of importance that “a page is important if important pages link to it,” HITS uses a mutually recursive deﬁnition of two concepts: “**a page is a good hub if it links to good authorities, and a page is a good authority if it is linked to by good hubs.**”

## Computation
We assign two scores to each Web page. One score prepresents the **hubbiness** of a page (the degree to which it is a good hub), and the second score represents **authority** of a page (the degree to which the it is a good authority).

$$h=\lambda \mu LL^T h$$
$$a=\lambda \mu L^T L a$$
where $\lambda$ is an unknown constant representing the scaling factor needed, $\mu$ is another scaling constant.

$$a=L^T h$$
$$h=La$$

HITS does not need to address the dead ends, spider traps and ohter graph issues.
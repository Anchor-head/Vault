# Decision trees
### What is a decision tree?
---
A decision tree is an algorithm that categorizes data by its attributes to predict the target variable; in other words, a decision tree groups people/data points in boxes based on their characteristics to judge them; scientific stereotyping, if you will. For example, if we are using a decision tree to predict whether a borrower will default on their loan, the decision tree will first profile the borrower based on relevant attributes (e.g. marital status, employment status, home ownership, etc.) to make a best guess based on how often other people with this same profile have defaulted. Here is a simple example of what such a decision tree might look like:

![[Pasted image 20250129223301.png]]

But how does a decision tree learn which attributes are relevant?
### Growing decision trees: the basics
---
A decision tree starts off as a root; at this stage, the tree is perfectly indiscriminate, that is, everyone looks the same to it.

**The first step in branching out** involves choosing a variable based on which to start discriminating. In the best case scenario, this variable would be a perfect indicator of our outcome variable; every celibate always defaults on their loan, and every married person always pays it back. This would result in an extremely *pure* division, and while reality is often messier than this, the point is that the tree branches in the direction that creates the purest division — the purity of the resulting leaf nodes is the tree’s objective function. 

**The two most common metrics** used to quantify a tree’s purity are entropy (algorithms: ID3 or C4.5) and the Gini coefficient (algorithm: CART).
##### [[Key concepts#^entropy|Entropy]]
![[Key concepts#^entropy]]
A decision tree based on entropy, or information gain (which is loss in entropy) branches out in the direction that minimizes the weighted sum of the entropies of the tree's leaf nodes. Here is [[Pasted image 20250130005758.png|a simple example]] of the calculation of the weighted entropies of three leaves of a tree.
##### [[Key concepts#^gini|Gini]] coefficient
![[Key concepts#^Gini]]
Just like entropy, a decision tree based on the Gini coefficient branches out in whatever way minimizes the weighted average of the Gini of the tree’s leaves.
#### What about continuous variables? 

If decision trees work by categorization, how do they deal with non-categorical or continuous variables?

Well, they make two categories out of the continuous variables, one category for values higher than a threshold, and the other for the rest.

The threshold is not chosen arbitrarily: it is chosen to maximize purity.
## Refining decision trees
---
Branching out almost always leads to *some* information gain; however, letting a tree grow indefinitely can easily lead to overfitting. Here are some common methods used to counter overfitting.

##### Parameter limits
The simplest way to prevent overfitting is to set hard limits on how far the tree can grow. This can be done by imposing a minimum leaf size, by putting a ceiling on the number of leaves the tree can have, or by setting a limit on the tree’s depth.
##### Trimming
The most computationally expensive  can grow decision trees all the way and trim off the node that minimize the # of mistakes saved/removed by # of nodes added. Iterate until the whole tree is trimmed off, at each step saving the tree for testing; at the end, test all trees on training and dev set and select the tree which performs best on the dev set.


# Chapter 2


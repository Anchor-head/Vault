# 1. Decision trees
## 1.1 What is a decision tree?
---
A decision tree is an algorithm that categorizes data by its attributes to predict the target variable; in other words, a decision tree groups people/data points in boxes based on their characteristics to judge them; scientific stereotyping, if you will. For example, if we are using a decision tree to predict whether a borrower will default on their loan, the decision tree will first profile the borrower based on relevant attributes (e.g. marital status, employment status, home ownership, etc.) to make a best guess based on how often other people with this same profile have defaulted. Here is a simple example of what such a decision tree might look like:

![[Pasted image 20250129223301.png|500]]

But how does a decision tree learn which attributes are relevant?
## 1.2 Growing decision trees: the basics
---
A decision tree starts off as a root; at this stage, the tree is perfectly indiscriminate, that is, everyone looks the same to it.

**The first step in branching out** involves choosing a variable based on which to start discriminating. In the best case scenario, this variable would be a perfect indicator of our outcome variable; every celibate always defaults on their loan, and every married person always pays it back. This would result in an extremely *pure* division, and while reality is often messier than this, the point is that the tree branches in the direction that creates the purest division — the purity of the resulting leaf nodes is the tree’s objective function. 
#### Measuring impurity
Two common metrics are used to quantify a tree’s purity: [[Key concepts#^entropy|entropy]] (algorithms: ID3 or C4.5) and the [[Key concepts#^gini|Gini coefficient]] (algorithm: CART).

![[Key concepts#^entropy]]
![[Key concepts#^Gini]]
Whichever metric is used, the tree always branches out in the direction that minimizes the weighted sum of the impurity of the tree's leaves. Here is [[Pasted image 20250130005758.png|a simple example]] of the calculation of the weighted entropies of three leaves of a tree, which would be summed to determine the entropy of the whole tree.
#### What about continuous variables? 

If decision trees work by categorization, how do they deal with non-categorical or continuous variables?

Well, they make two categories out of the continuous variables, one category for values higher than a threshold, and the other for the rest.

The threshold is not chosen arbitrarily: it is chosen to maximize purity.

More than two categories can be created by further subdividing either side of the continuous variable in the same way, like a binary decision tree.
## 1.3 Refining decision trees
---
Branching out almost always leads to *some* information gain; however, letting a tree grow indefinitely can easily lead to overfitting. Here are some common methods used to counter overfitting.
##### Parameter limits
The simplest way to prevent overfitting is to set hard limits on how far the tree can grow. This can be done by imposing a minimum leaf size, putting a ceiling on the number of leaves the tree can have, or setting a limit on the tree’s depth.
##### Trimming
The most computationally extravagant way to mitigate overfitting is to grow the decision tree all the way out, test it on the development set, and trim off the least valuable branch; test it again on the development set, and trim the least valuable remaining branch, and so on until only the root is left. Keep the tree that performed best on the development set.
>[!info] A branch’s value
>A branch’s value is quantified by: $$\dfrac{\#\ mistakes\ saved}{\#\ nodes\ added}$$

# 2.


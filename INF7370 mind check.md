# Decision trees
### What is a decision tree?
---
A decision tree is an algorithm that categorizes data by its attributes to predict the target variable; in other words, a decision tree groups people/data points in boxes based on their characteristics to judge them; scientific stereotyping, if you will. For example, if we are using a decision tree to predict whether a borrower will default on their loan, the decision tree will first profile the borrower based on relevant attributes (e.g. marital status, employment status, home ownership, etc.) to make a best guess based on how often other people with this same profile have defaulted. Here is a simple example of what such a decision tree might look like:

![[Pasted image 20250129223301.png]]

But how does a decision tree learn which attributes are relevant?
### Growing decision trees: the basics
---
A decision tree starts off as a root; at this stage, the tree is perfectly indiscriminate, that is, every data point looks the same to it.

**The first step in branching out** involves choosing a variable based on which to discriminate. Ideally, the variable chosen will be such that different values of this variable correlate with different values of the target variable; the greater this correlation, the greater the branch's explanatory power. 

**There are two possible metrics** to quantify the discriminatory power a branch provides: information gain (algorithms: ID3 or C4.5) and Gini (algorithm: CART).
###### Information gain
Information gain is synonymous with loss of entropy.
![[Key concepts#^entropy]]
A decision tree based on information gain branches out in the direction that minimizes entropy, or more specifically, the weighted sum of the entropies of the tree's leaf nodes. Here is [[Pasted image 20250130005758.png|a simple example]] of such a calculation.

###### Gini coefficient
The Gini coefficient is a less computationally expensive measure of purity, due to its lack of logarithms.
$$
Gini = 1- \sum_{i=1}^C {p_i}^2
$$
**Purest set:** Gini = 0

**Least pure set:** Gini approaches 1




### What about continuous variables? 

Make two categories out of the continuous variables, defined by a threshold; split the data into two categories depending on whether 

The threshold (in this example, 100k) is not chosen arbitrarily: it is chosen to maximize entropy/gini.

  

  

## Trimming decision trees

You can grow decision trees all the way and trim off the node that minimize the # of mistakes saved/removed by # of nodes added. Iterate until the whole tree is trimmed off, at each step saving the tree for testing; at the end, test all trees on training and dev set and select the tree which performs best on the dev set.


# Chapter 2


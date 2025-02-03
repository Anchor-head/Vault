
# 🤔 What is a decision tree?
---
A decision tree is an algorithm that categorizes data by its attributes to predict the target variable; in other words, a decision tree groups people/data points in boxes based on their characteristics to judge them; ==scientific stereotyping==, if you will. For example, if we are using a decision tree to predict whether a borrower will default on their loan, the decision tree will first profile the borrower based on relevant attributes (e.g. marital status, employment status, home ownership, etc.) to make a best guess based on how often other people with this same profile have defaulted. Here is a simple example of what such a decision tree might look like:

![[Pasted image 20250129223301.png|500]]

But how does a decision tree learn which attributes are relevant?





# 🌳 Growing a decision tree: the basics
---
A decision tree starts off as a root; at this stage, the tree is perfectly indiscriminate, that is, every data point looks the same to it.

**The first step in branching out** a tree involves choosing a variable based on which to discriminate. In the best case scenario, this variable would be a perfect indicator of our outcome variable; every celibate always defaults on their loan, and every married person always pays it back. This would result in an extremely clean, or *pure*, division, and this purity is precisely what growing trees are after — indeed, ==the tree will decide which variable to discriminate by purely based on the purity of the resulting split==.
#### Measuring impurity
Two common measures of impurity are [[Key concepts#^entropy|entropy]] (algorithms: ID3 or C4.5) and the [[Key concepts#^gini|Gini coefficient]] (algorithm: CART).

![[Key concepts#^entropy]]
![[Key concepts#^Gini]]
Whichever metric is used, a tree will always branch out in the direction that minimizes the tree's impurity, which is the weighted sum of the impurity of the tree's leaves ([[Pasted image 20250203171830.png|here is the formula using Gini from CART]], and an [[Pasted image 20250130005758.png|example calculation using entropy]]).
#### What about continuous variables? 

If decision trees work by categorization, how do they deal with non-categorical or continuous variables?

Indeed, they can't; you have to **discretize** the continuous variable, by splitting it into chunks that each contain a certain range of that continuous variable.

Start by making two categories out of the continuous variable: one category for values above a certain threshold, and one for values below. But this threshold is chosen to minimize impurity according to the usual formula ([[Pasted image 20250203025627.png|example]] using Scikit-Learn's [[Pasted image 20250203165419.png|CART algorithm loss function, or weighted Gini]]).

More than two subcategories can be created by recursively subdividing the data on either side of the threshold with another threshold, similar in functioning to a binary tree.
# ✂️ Refining decision trees
---
Branching out almost always leads to *some* information gain; however, letting a tree grow indefinitely can easily lead to overfitting. Here are some common methods used to counter overfitting.
#### Parameter limits
The simplest way to prevent overfitting is to set hard limits on how far the tree can grow. This can be done by ==imposing a minimum leaf size, putting a ceiling on the number of leaves the tree can produce, or setting a limit on the tree’s depth==.
#### Trimming
The most computationally extravagant way to mitigate overfitting is to grow the decision tree all the way out, test it on the development set, trim off the least valuable branch (as defined below), and test it again on the development set; again trim off the least valuable remaining branch, and test again, and so on until only the root is left. Keep the tree that performed best on the development set.
>[!info] A branch’s value
>A branch’s value is quantified by: $$\dfrac{\#\ mistakes\ saved}{\#\ leaves\ added}$$


# 📈Regression trees
---
Decision trees can also be used to predict continuous variables. Every leaf node's prediction is the mean value of all training data in the leaf node, and the loss function is MSE instead of impurity.
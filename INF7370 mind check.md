# Decision trees
A decision tree is an algorithm that categorizes data by its attributes in order to help predict a certain target variable. For example, if we are using a decision tree to predict whether a borrower will default of their loan or not, the decision tree will profile the borrower by relevant attributes (e.g. marital status, employment status, etc.) to make a best guess as to whether they will default on their loan or not. Here is a simple example of what such a decision tree might look like:

![[Pasted image 20250129223301.png]]

During training, a decision tree learns which attributes (independent variables) help discriminate between outcomes.
## Growing decision trees
TWO POSSIBLE METRICS for growing trees:

1. Information gain (algorithms: ID3 or C4.5)
2. Gini (algorithm: CART)
### Information gain
Information gain is a reduction in entropy. Entropy is a measure of the impurity of a certain set.

**Purest set:** entropy = 0, all elements belong to one class

**Least pure set:** high entropy, elements are evenly distributed among many different classes

A tree seeks to grow in the direction that minimizes entropy, at every step.
#### Entropy calculation
The tree's entropy is the weighted sum of the entropies of its leaf nodes (Figure 3); the entropy of a leaf node is the weighted sum of the self-informations (in Shannons) of all possible outcomes (Figure 1).

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeoVHykaGhGrim0MAP8SFOwCaBPpaAxlD2V094azsOa3cAZZVMz9exps4psTgZSe2h7MhjfiamTWtYnTH5R2iavq21VVyvnQQGw0mVF_3FbebgLThkUXuBj0sUaDzR4wo5z7s07lg?key=tcv5BltTjCsL69XLxwWUykjz)
***Figure 1:** formula for the entropy of an undivided set or of a leaf node.* 

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfAefJ44Wp1X0svXHAV_l1u12J-bTjgeFBjru0kqpg6P3zDke-V9LiGq-nEevMKuw5_6FY0ki4eD6kPv80ukz5GOqlfPkA-3UxfQnkdhcc9NVscs8_zIatC5mTpzAAbOKQkLFp9DA?key=tcv5BltTjCsL69XLxwWUykjz)
***Figure 2:** an entropy calculation (with respect to "Defaulted Borrower" as the outcome) for a small dataset.*

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXduRMvTD9iVD4P4LPvDCkzZquhTBZ9i1mbZEZ2q-CJVG5k3ah_q6YwA-hs7n9HH0wi6dvBuX-e1O7lfemiyeVqGoaNeh29ZJrsrmt4HruGD119w8_3s8jHKeKGXPwgkSaJhFv0Jig?key=tcv5BltTjCsL69XLxwWUykjz)![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXd3JZPSRwoN1Bx-Kf5KJrbu35noVEwUV5_rqzIZ9dL75tk15VP_SPXvD_4wklieLxvbMmkd8zdolvHZ65n7k79h9LnLlBXxVoy_o92FHIaQfKcaH-zUfxtF5YPn_gHBpgZSMq7a?key=tcv5BltTjCsL69XLxwWUykjz)
***Figure 3:** weighted entropy calculation for each leaf node of a 3-leaf decision tree; the tree’s final entropy is the sum of these weighted entropies.*

### Gini coefficient
The Gini coefficient is a less computationally expensive measure of purity, due to its lack of logarithms.
$1-sigma(5)$
$$
1-(p_i^2)
$$

### What about continuous variables? 

Make two categories out of the continuous variables, defined by a threshold; split the data into two categories depending on whether 

The threshold (in this example, 100k) is not chosen arbitrarily: it is chosen to maximize entropy/gini.

  

  

## Trimming decision trees

You can grow decision trees all the way and trim off the node that minimize the # of mistakes saved/removed by # of nodes added. Iterate until the whole tree is trimmed off, at each step saving the tree for testing; at the end, test all trees on training and dev set and select the tree which performs best on the dev set.
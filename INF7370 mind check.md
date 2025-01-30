# Decision trees

A decision tree is an algorithm that categorizes data by its attributes in order to help predict a certain target variable. For example, if we are using a decision tree to predict whether a borrower will default of their loan or not, the decision tree will profile the borrower by relevant attributes (e.g. marital status, employment status, etc.) to make a best guess as to whether they will default on their loan or not. 

During training, a decision tree learns which attributes (independent variables) help discriminate between outcomes. 
## Growing decision trees

TWO POSSIBLE METRICS:

1. Information gain (algorithms: ID3 or C4.5)
2. Gini (algorithm: CART)
### Information gain: the tree’s loss function

Information gain is a reduction in entropy. Entropy is a measure of the impurity of a certain set:

**Purest set:** entropy = 0, all elements belong to one class

**Least pure set:** high entropy, elements are evenly distributed among many different classes

By default, the entropy of a set is the weighted sum of the self-informations (in bits/Shannons) of all possible outcomes: 

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeoVHykaGhGrim0MAP8SFOwCaBPpaAxlD2V094azsOa3cAZZVMz9exps4psTgZSe2h7MhjfiamTWtYnTH5R2iavq21VVyvnQQGw0mVF_3FbebgLThkUXuBj0sUaDzR4wo5z7s07lg?key=tcv5BltTjCsL69XLxwWUykjz)
Example (with Defaulter Borrower as the outcome variable):
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfAefJ44Wp1X0svXHAV_l1u12J-bTjgeFBjru0kqpg6P3zDke-V9LiGq-nEevMKuw5_6FY0ki4eD6kPv80ukz5GOqlfPkA-3UxfQnkdhcc9NVscs8_zIatC5mTpzAAbOKQkLFp9DA?key=tcv5BltTjCsL69XLxwWUykjz)
A growing decision tree seeks to have the purest possible leaf nodes — its objective function is the weighted sum of the entropies of its leaf nodes:
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXduRMvTD9iVD4P4LPvDCkzZquhTBZ9i1mbZEZ2q-CJVG5k3ah_q6YwA-hs7n9HH0wi6dvBuX-e1O7lfemiyeVqGoaNeh29ZJrsrmt4HruGD119w8_3s8jHKeKGXPwgkSaJhFv0Jig?key=tcv5BltTjCsL69XLxwWUykjz)![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXd3JZPSRwoN1Bx-Kf5KJrbu35noVEwUV5_rqzIZ9dL75tk15VP_SPXvD_4wklieLxvbMmkd8zdolvHZ65n7k79h9LnLlBXxVoy_o92FHIaQfKcaH-zUfxtF5YPn_gHBpgZSMq7a?key=tcv5BltTjCsL69XLxwWUykjz)


### Gini coefficient

Entropy is computationally

### What about continuous variables? 

Make two categories out of the continuous variables, defined by a threshold; split the data into two categories depending on whether 

The threshold (in this example, 100k) is not chosen arbitrarily: it is chosen to maximize entropy/gini.

  

  

## Trimming decision trees

You can grow decision trees all the way and trim off the node that minimize the # of mistakes saved/removed by # of nodes added. Iterate until the whole tree is trimmed off, at each step saving the tree for testing; at the end, test all trees on training and dev set and select the tree which performs best on the dev set.
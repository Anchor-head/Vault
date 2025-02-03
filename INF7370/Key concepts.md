
> [!info] Entropy
> Entropy is a measure of the degree of impurity or diversity in a set; the more impure the set, the greater the entropy, while a perfectly pure set (a set where all elements belong to the same class) has zero entropy.
> #### $$Entropy = -\sum_{i\in C}p_i*log_2(p_i)$$
> *Where $C$ represents the set of all classes (in this case, a class stands for a value that the target variable can take) and $p_i$ represents the proportion of class $i$ in the data.*
> 
> >[!tip] Intuition
> >Entropy is the expected self-information (in Shannons) of a set, that is, the weighted sum of the Shannon informations of every outcome in the set — hence why a loss of entropy is termed =="information gain"==. ^entropy

>[!info] Gini coefficient
>The Gini coefficient is a measure of the degree of impurity or diversity in a set; it approaches 1 as impurity increases, and is 0 for a perfectly pure set.
>$$Gini = 1- \sum_{i\in C} {p_i}^2$$
>*Where $C$ represents the set of all classes (in this case, a class stands for a value that the target variable can take) and $p_i$ represents the proportion of class $i$ in the data.*
>
>>[!tip] Advantage
>> Gini is a less computationally expensive measure of purity than entropy due to its lack of logarithms. ^Gini

$A$ = Attribute, $t_A$ = threshold
![[Pasted image 20250203165419.png]]
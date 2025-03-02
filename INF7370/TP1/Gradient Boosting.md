
Le Gradient Boosting (GBoost) est une méthode d'apprentissage machine qui produit un ensemble d'arbres de régression que l'on additionne pour obtenir une prédiction. Les arbres sont entrainés séquentiellement, où chaque nouvel arbre tâche à prédire les résidus de l'ensemble d'arbres précédents. Par exemple, si le premier arbre n'a qu'une feuille et prédit la variable dépendante $y$ par la moyenne de ses éléments, $\hat{y}_1=\bar{y}_1$, alors le deuxième arbre a pour objectif de prédire les résidus produits par le premier arbre, $r_1=y_1-\bar{y}_1$. L'addition des prédictions du deuxième arbre au premier raffine la prédiction de l'ensemble; $\hat{y}_2=\hat{y}_1+\nu*\hat{r}_1=\bar{y}_1+\nu*\hat{r}_1$ est une meilleure prédiction que $\hat{y}_1=\bar{y}_1$. Ensuite, le troisième arbre prédira les résidus du dernier arbre, et sera ajouté à l'ensemble de la même manière pour en raffiner la prédiction.

![[Pasted image 20250302165348.png]]
*Source de l'image: https://www.geeksforgeeks.org/ml-gradient-boosting/*


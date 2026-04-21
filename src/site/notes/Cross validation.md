---
{"dg-publish":true,"permalink":"/cross-validation/","dgPassFrontmatter":true}
---


# Que es 
Es una robusta técnica de machine learning utilizada para evaluar el rendimiento de un modelo y ver qué tan bien generaliza un modelo estadístico a un conjunto de datos independiente.

Entre las técnicas mas utilizadas están el K-fold cross validation, Stratified k-fold cross validation, y Leave-One-Out (LOO)
# K-fold cross validation
Es un metodo para evaluar el desarrollo de un modelo de machine learning partiendo la data en k subsets o llamados "folds" de igual tamaño. El modelo será entrenado con k-1 folds y testeados con folds restantes. El proceso será repetido k veces. El desarrollo del modelo será el promedio de las k iteraciones.
![Pasted image 20260203224415.png](/img/user/attachments/Pasted%20image%2020260203224415.png)
```python
from sklearn import datasets  
from sklearn.tree import DecisionTreeClassifier  
from sklearn.model_selection import KFold, cross_val_score  
  
X, y = datasets.load_iris(return_X_y=True)  
  
clf = DecisionTreeClassifier(random_state=42)  
  
k_folds = KFold(n_splits = 5)  
  
scores = cross_val_score(clf, X, y, cv = k_folds)  
  
print("Cross Validation Scores: ", scores)  
print("Average CV Score: ", scores.mean())  
print("Number of CV Scores used in Average: ", len(scores))
```
# Stratified k-fold cross validation
Stratified k-fold cross validation es un metodo de cross-validation que asegura que la proporcion de ejemplos para cada clase es aproximadamente el mismo para cada fold.
Esto es muy útil cuando la clase de distribución es debalanceada, lo que significa que hay diferentes numeros de muestras para cada clase.
Supon que tienes 1000 transacciones de las cuales 950 son legitimas y 50 son falsas, si divides 1000 datos en 5 grupos de forma aleatoria, puede pasar que un grupo no haya ninguna que sea fraude.
Aquí es donde viene Stratified k-fold donde obliga a que cada uno de los 5 grupos tenga exactamente la misma proporción
- Cada grupo de 200 transacciones tendrá 190 legítimas y 10 fraudes.
- Así, el modelo siempre es evaluado con casos de fraude en cada iteración, dando una métrica real de su capacidad para detectar un crimen.
![Pasted image 20260203225354.png](/img/user/attachments/Pasted%20image%2020260203225354.png)
```python
from sklearn import datasets  
from sklearn.tree import DecisionTreeClassifier  
from sklearn.model_selection import StratifiedKFold, cross_val_score  
  
X, y = datasets.load_iris(return_X_y=True)  
  
clf = DecisionTreeClassifier(random_state=42)  
  
sk_folds = StratifiedKFold(n_splits = 5)  
  
scores = cross_val_score(clf, X, y, cv = sk_folds)  
  
print("Cross Validation Scores: ", scores)  
print("Average CV Score: ", scores.mean())  
print("Number of CV Scores used in Average: ", len(scores))
```


# Referencias
https://ompramod.medium.com/cross-validation-623620ff84c2
# Enlaces
[[Machine Learning\|Machine Learning]]
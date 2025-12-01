# Chapter 6. Decision Trees

Decision trees are versatile machine learning algorithms that can perform both classification and regression tasks, and even multioutput tasks. They are powerful algorithms, capable of fitting complex datasets.

Decision trees are also the fundamental components of random forests, which are among the most powerful machine learning algorithms available today.

## Training and Visualizing a Decision Tree

The following code trains a DecisionTreeClassifier on the iris dataset

```python
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier
iris = load_iris(as_frame=True)
X_iris = iris.data[["petal length (cm)", "petal width (cm)"]].values
y_iris = iris.target
tree_clf = DecisionTreeClassifier(max_depth=2, random_state=42)
tree_clf.fit(X_iris, y_iris)
```



The trained decision tree can be visualized by first using the export_graphviz() function to output a graph definition file called iris_tree.dot:

```python
from sklearn.tree import export_graphviz
export_graphviz(
tree_clf,
out_file="iris_tree.dot",
feature_names=["petal length (cm)", "petal width (cm)"],
class_names=iris.target_names,
rounded=True,
filled=True
)
```



## Making Predictions

Suppose you find an iris flower and you want to classify it based on its petals. You start at the root node
(depth 0, at the top): this node asks whether the flower’s petal length is smaller than 2.45 cm. If it is, then you move down to the root’s left child node (depth 1, left). In this case, it is a leaf node (i.e., it does not have any child nodes), so it does not ask any questions: simply look at the predicted class for that node, and the decision tree predicts that your flower is an Iris setosa (class=setosa).
Now suppose you find another flower, and this time the petal length is greater than 2.45 cm. You again start at the root but now move down to its right child node (depth 1, right). This is not a leaf node, it’s a split node, so it asks another question: is the petal width smaller than 1.75 cm? If it is, then your flower is most likely an Iris versicolor (depth 2, left). If not, it is likely an Iris virginica (depth 2, right). It’s really that simple.


## Estimating Class Probabilities
A decision tree can also estimate the probability that an instance belongs to a partic‐
ular class k. First it traverses the tree to find the leaf node for this instance, and
then it returns the ratio of training instances of class k in this node. For example,
suppose you have found a flower whose petals are 5 cm long and 1.5 cm wide. The
corresponding leaf node is the depth-2 left node, so the decision tree outputs the
following probabilities: 0% for Iris setosa (0/54), 90.7% for Iris versicolor (49/54), and
9.3% for Iris virginica (5/54). And if you ask it to predict the class, it outputs Iris
versicolor (class 1) because it has the highest probability. Let’s check this:
```python
>>> tree_clf.predict_proba([[5, 1.5]]).round(3)
array([[0.
, 0.907, 0.093]])
>>> tree_clf.predict([[5, 1.5]])
array([1])
```
## Gini Impurity or Entropy?

By default, the DecisionTreeClassifier class uses the Gini impurity measure, but
you can select the entropy impurity measure instead by setting the criterion hyper‐
parameter to "entropy". The concept of entropy originated in thermodynamics as
a measure of molecular disorder: entropy approaches zero when molecules are still
and well ordered. Entropy later spread to a wide variety of domains, including in
Shannon’s information theory, where it measures the average information content of
a message, as we saw in Chapter 4. Entropy is zero when all messages are identical. In
machine learning, entropy is frequently used as an impurity measure: a set’s entropy
is zero when it contains instances of only one class.

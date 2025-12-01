# CHAPTER 2

# End-to-End Machine Learning Project

Main steps to walk through for a machine learning project:

1. Look at the big picture.
2. Get the data.
3. Explore and visualize the data to gain insights.
4. Prepare the data for machine learning algorithms.
5. Select a model and train it.
6. Fine-tune your model.
7. Present your solution.
8. Launch, monitor, and maintain your system.



## Working with Real Data

For learning about machine learning, it is best to experiment with real-world data, not artificial datasets.

Popular open data repositories:

* OpenML.org
* Kaggle.comn
* PapersWithCode.com
* UC Irvine Machine Learning Repository
* Amazon’s AWS datasets
* TensorFlow datasets



Meta portals (they list open data repositories):

* DataPortals.org
* OpenDataMonitor.eu

Other pages listing many popular open data repositories:

* Wikipedia’s list of machine learning datasets
* Quora.com
* The datasets subreddit

## Look at the Big Picture

The goal is use a California census data to build a model of housing prices in the state. This data includes metrics such as the population, median income, and median housing price for each block group in California. Block groups are the smallest geographical unit for which the US Census Bureau publishes sample data (a block group typically has a population of 600 to 3,000 people), “districts” for short.

The model should learn from this data and be able to predict the median housing price in any district, given all the other metrics.

### Frame the Problem 

Knowing the objective is important because it will determine how you frame the problem, which algorithms you will select, which performance measure you will use to evaluate your model, and how much effort you will spend tweaking it.

Have you found the answers? Let’s see. This is clearly a typical supervised learning task, since the model can be trained with labeled examples (each instance comes with the expected output, i.e., the district’s median housing price). It is a typical regression task, since the model will be asked to predict a value. More specifically, this is a multiple regression problem, since the system will use multiple features to make a prediction (the district’s population, the median income, etc.). It is also a univariate regression problem, since we are only trying to predict a single value for each district.

### Select the Performance Measure

A typical performance measure for regression problems is the root mean square error (RMSE). It gives an idea of how much error the system typically makes in its predictions, with a higher weight given to large errors.


$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$


## Get Data

### Download the Data

In typical environments your data would be available in a relational database or some other common data store, and spread across multiple tables/documents/files.

Here is the function to fetch and load the data:

```python
from pathlib import Path
import pandas as pd
import tarfile
import urllib.request

def load_housing_data():
    tarball_path = Path("datasets/housing.tgz")
    if not tarball_path.is_file():
        Path("datasets").mkdir(parents=True, exist_ok=True)
        url = "https://github.com/ageron/data/raw/main/housing.tgz"
        urllib.request.urlretrieve(url, tarball_path)
        with tarfile.open(tarball_path) as housing_tarball:
        	housing_tarball.extractall(path="datasets")
	return pd.read_csv(Path("datasets/housing/housing.csv"))
housing = load_housing_data()
```



When load_housing_data() is called, it looks for the datasets/housing.tgz file. If it does not find it, it creates the datasets directory inside the current directory (which is /content by default, in Colab), downloads the housing.tgz file from the ageron/data GitHub repository, and extracts its content into the datasets directory; this creates the datasets/housing directory with the housing.csv file inside it. Lastly, the function loads this CSV file into a Pandas DataFrame object containing all the data, and returns it.







# Reference

## GitHub

​	https://github.com/ageron/handson-ml3/blob/main/02_end_to_end_machine_learning_project.ipynb

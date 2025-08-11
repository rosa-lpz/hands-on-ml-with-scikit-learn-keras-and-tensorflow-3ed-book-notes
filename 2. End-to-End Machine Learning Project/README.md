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

Data

## Working with Real Data

For learning about machine learning, it is best to experiment with real-world data, not artificial datasets.



## Download the Data

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

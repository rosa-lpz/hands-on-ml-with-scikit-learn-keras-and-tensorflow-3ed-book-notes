# The Machine Learning Landscape

## What Is Machine Learning?

Machine Learning is the science (and art) of programming computers so they can
learn from data.

Here is a slightly more general definition:
	[Machine Learning is the] field of study that gives computers the ability to learn without being explicitly programmed.
	—Arthur Samuel, 1959

And a more engineering-oriented one:
	A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E. 

​	—Tom Mitchell, 1997



## Why Use Machine Learning?
Machine learning is great for:
* Problems for which existing solutions require a lot of fine-tuning or long lists of rules (a machine learning model can often simplify code and perform better than the traditional approach)
* Complex problems for which using a traditional approach yields no good solution (the best machine learning techniques can perhaps find a solution)
* Fluctuating environments (a machine learning system can easily be retrained on new data, always keeping it up to date)
* Getting insights about complex problems and large amounts of data

  
## Examples of Applications
Here are some concrete examples of Machine Learning tasks, along with the techniques that can tackle them:

* Analyzing images of products on a production line to automatically classify them
  *  This is image classification, typically performed using convolutional neural networks (CNNs; see Chapter 14) or sometimes transformers (see Chapter 16).
* Detecting tumors in brain scans
  * This is semantic segmentation, where each pixel in the image is classified (as we want to determine the exact location and shape of tumors), typically using CNNs or transformers.
* Detecting credit card fraud
  * This is anomaly detection, which can be tackled using isolation forests, Gaussian mixture models (see Chapter 9), or autoencoders (see Chapter 17).

* 

## Types of Machine Learning Systems

There are so many different types of machine learning systems that it is useful to classify them in broad categories, based on the following criteria:
* How they are supervised during training (supervised, unsupervised, semi-supervised, self-supervised, and others)
* Whether or not they can learn incrementally on the fly (online versus batch learning)
* Whether they work by simply comparing new data points to known data points, or instead by detecting patterns in the training data and building a predictive model, much like scientists do (instance-based versus model-based learning)

These criteria are not exclusive; you can combine them in any way you like. For example, a state-of-the-art spam filter may learn on the fly using a deep neural net‐ work model trained using human-provided examples of spam and ham; this makes it an online, model-based, supervised learning system.



## Main Challenges of Machine Learning

In short, since your main task is to select a model and train it on some data, the two things that can go wrong are “bad model” and “bad data”. Let’s start with examples of bad data.



### Insufficient Quantity of Training Data

Machine learning takes a lot of data for most machine learning algorithms to work properly. Even for very simple problems you typically need thousands of examples, and for complex problems such as image or speech recognition you may need millions of examples (unless you can reuse parts of an existing model).



### Poor-Quality Data

Obviously, if your training data is full of errors, outliers, and noise (e.g., due to poor- quality measurements), it will make it harder for the system to detect the underlying patterns, so your system is less likely to perform well. It is often well worth the effort to spend time cleaning up your training data.

### Irrelevant Features

As the saying goes: garbage in, garbage out. Your system will only be capable of learning if the training data contains enough relevant features and not too many irrelevant ones. A critical part of the success of a machine learning project is coming up with a good set of features to train on. This process, called feature engineering, involves the following steps:

* Feature selection (selecting the most useful features to train on among existing features)
* Feature extraction (combining existing features to produce a more useful one—as we saw earlier, dimensionality reduction algorithms can help)
* Creating new features by gathering new data

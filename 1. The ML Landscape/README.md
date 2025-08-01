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
Let’s look at some concrete examples of Machine Learning tasks, along with the tech‐
niques that can tackle them:

* Analyzing images of products on a production line to automatically classify them
  *  This is image classification, typically performed using convolutional neural networks (CNNs; see Chapter 14).
* Detecting tumors in brain scans
  * This is semantic segmentation, where each pixel in the image is classified (as we
    want to determine the exact location and shape of tumors), typically using CNNs
    as well.

## Types of Machine Learning Systems

There are so many different types of machine learning systems that it is useful tov classify them in broad categories, based on the following criteria:
* How they are supervised during training (supervised, unsupervised, semi-supervised, self-supervised, and others)
* Whether or not they can learn incrementally on the fly (online versus batch learning)
* Whether they work by simply comparing new data points to known data points, or instead by detecting patterns in the training data and building a predictive model, much like scientists do (instance-based versus model-based learning)

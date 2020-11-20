# Exercise 3: Shared Task

In this exercise, you will make first experiments with Weka. To this end, you'll find a dataset in the form of an ARFF file in this repository (and you'll need to install Weka from [here](https://www.cs.waikato.ac.nz/ml/weka/index.html)). The dataset consists of an annotated part of the Leiden des jungen Werther, by J.W.v. Goethe. Annotated are entity references, i.e., mentions of characters, locations (and very few others). In NLP-terms, this is situated in between named entity recognition (because NP mentions are also annotated) and coreference resolution (because pronouns are not annotated). 

The data set you've been given can be used as a training data set. A second data set (another part of the same text) will be used as a withheld test set (to be evaluated against next week). These are the basic ingredients of a shared task. Think of the unknown test set as the "real world" in which our models are expected to work.

Your task is to use Weka to establish a best performing model on the training data. 

## Cross validation

The results you will see on the test data will be lower than on the training data. This is normal. You can minimize this effect if you use cross validation (Experimenter > Classify > Test options). Beware that cross validation includes a random distribution of the data, you will most likely get slightly different results with each run.

## Features
As you will find out, the data set includes many features, some of them are not really useful, some may hurt the performance. Feel free to turn them off as you like. But take notes, because you will need to reproduce these on the real test data set.

## Classifier parameters
Most classifiers have parameters that you can set (so called hyper-parameters, because they are not trained). Feel free to play around with them -- but again, take notes.

## Submission and Evaluation
On November 24, 11:55, I will push the test data to the repository. In next week's session, you will then pull the test data via git, and apply your model (via Experimenter > Classify > Test options) to this new data set. We will then collect performance scores from all partipants during the session -- and discuss all upcoming issues and questions. 

## Hints and Tips (added Nov. 20)

This task and data set provides a few challenges, some technical and some conceptual:

1. Strings: As we have discussed, many features in the data set are string values. And you may have noticed that many algorithms cannot really deal with string features. You will need to deal with these by either a) convert string features into nominal ones (using the filter `weka.filters.unsupervised.attribute.StringToNominal`) or b) convert some or all string features into word vectors (using `weka.filters.unsupervised.StringToWordVector`, which yields many more new features, see documentation for details).
2. Many words (and subsequently, nominal feature values) appear only once or twice. It might be a good idea to remove those. There is, of course, a filter for that.
3. Skewed data set: The data set is highly skewed, i.e., there are not many positive instances, but a lot of negative ones. This is a regular problem for NLP, because many interesting phenomena are rare. There are different strategies to deal with that, one of them is to oversample the unterrepresented classes by just duplicating instances until an equal representation in the training data is reached.
4. If you need to read up on the BIO scheme, this [Wikipedia page](https://en.wikipedia.org/wiki/Inside–outside–beginning_(tagging)) has you covered. I mentioned it briefly while talking about the exercise, but maybe it was to fast.

# Additional material

- You can find an in-depth description of the annotation process [here](https://doi.org/10.1515/9783110693973-010).
- The full list of features can be found in the file [`feature-table.pdf`](feature-table.pdf).


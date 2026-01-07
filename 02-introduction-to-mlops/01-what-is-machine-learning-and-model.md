# Fundamentals

### What Is Machine Learning?

Think of machine learning as teaching a computer to learn patterns from data instead of programming every rule manually.

With normal programming, you write rules yourself.
With machine learning, you give the computer examples, and it figures out the rules.

Example: Flower Species Prediction

Suppose you want a system that predicts whether a flower is Setosa, Versicolor, or Virginica based on features like:

Petal length

Petal width

Sepal length

Sepal width

You could try writing if-else conditions — but it's nearly impossible to capture every pattern.

Instead, you give the computer:

150 flower samples

Each sample has measurements

Each sample has the correct species label

The machine learning algorithm then learns the relationship between measurements and species.

That learned relationship is called a model.

### What Is a Model?

A model is the final output of machine learning.

It is not the data.
It is not the algorithm.
It is the pattern the algorithm learned from the data.

Think of the model as:

A mathematical function the computer created

It takes inputs (flower measurements)

It outputs predictions (species)

Example: Flower Species Model

After training, the model may learn things like:

If petal length is very small, it's likely Setosa.

If petal length is large and petal width is medium, it’s probably Virginica.

You never coded these rules.
The algorithm found them automatically based on the training data.

When you pass a new flower’s measurements into the model:

Input: Petal length = 5.1, Petal width = 1.8  
Output: Species = Versicolor


The model is simply applying what it learned earlier.


---

## 🧠 My Learning Notes

While going through this topic, my key understanding was:

- Machine Learning removes the need for writing endless if-else conditions.
- The real power of ML lies in how data helps the algorithm find patterns on its own.
- A trained model is nothing but a mathematical function that generalizes from data.

I rewrote this topic in my own simple words on Hashnode to make sure I truly understand it:

👉 Blog: https://hashnode.com/edit/cmk3pjdb5000202jraey25xuq


This repository is part of my **MLOps Zero to Hero learning journey**, where I document concepts as I learn them step by step.

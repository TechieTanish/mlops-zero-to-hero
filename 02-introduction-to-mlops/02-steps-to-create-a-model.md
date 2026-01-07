# How Data Scientists Create a Simple Model

Now that you know what machine learning is and what a model is, the next step is understanding how data scientists actually build one.
Think of this as the “hello world” of ML.

### Start with a Small Dataset

Every model begins with data.

Example:
You want to predict flower species based on features like:

Petal length

Petal width

Sepal length

Sepal width

This dataset will have:

Inputs (features): the measurements

Output (label): the species name

### Split the Data: Train vs Test

Before training, data scientists split the dataset into:

Training data (usually ~80%)
The part the model learns from.

Testing data (usually ~20%)
The part used later to check if the model learned properly.

Why?
Because you should never test a student with questions they already memorized.

### Choose a Simple Model

For beginners, data scientists usually start with a simple algorithm, like:

Logistic Regression (for classification)

Decision Tree

k-Nearest Neighbors (KNN)

For the flower species example, Logistic Regression or Decision Tree works great.

### Train the Model

Training means:

Give the model training data

Let it “learn” patterns between measurements and flower species

Internally, the model adjusts itself to reduce mistakes

You don’t manually code patterns.
The model learns them automatically.

### Test the Model

Now, evaluate it using the test data.

The goal is to see:

How many predictions are correct?

Where is the model making mistakes?

This step tells you if the model is ready or needs improvement.

### Improve (If Needed)

Beginners usually follow simple improvement steps:

Remove noisy or incorrect data

Try a different model

Tune settings (called hyperparameters)

Add more training samples

Even small changes can boost accuracy.

### Save the Model

Once the model performs well, you save it as a file.
Example formats:

.pkl

.joblib

.onnx

This saved model can now be used by:

Apps

Websites

Backend microservices

MLOps pipelines

This is what gets deployed.


---

## 🧠 My Learning Notes

While understanding the steps to create a Machine Learning model, I realized that ML is not just about training once and predicting forever.

My key takeaways:

- A dataset is the backbone of the entire ML process.
- Splitting data (80-20) helps us check whether the model actually learned or just memorized.
- Choosing the right algorithm directly impacts prediction accuracy.
- A model is created by mathematical functions during training.
- Testing is mandatory because a trained model can still give wrong results.
- Retraining is a normal and important part of ML when performance is poor.
- Saving the model (.pkl, .joblib, .onnx) makes it reusable in real applications.
- ML Engineers and Software Developers help move the model into production using APIs.

I explained this topic in my own simple language on Hashnode to strengthen my understanding:

👉 Blog: https://hashnode.com/edit/cmk3pjve5000202l56b3t56r7
This documentation is part of my **MLOps Zero to Hero learning journey**, where I break down concepts step by step as I learn them.

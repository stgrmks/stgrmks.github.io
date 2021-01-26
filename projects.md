---
layout: page
title: Projects
permalink: /projects/
---
<style>
body {
text-align: justify}
</style>
## Rodelbahn-Tracker <a href="https://github.com/stgrmks/Rodelbahn-Tracker" class="btn">![View on GitHub](/img/GitHub-Mark-32px.png "View on GitHub")</a>
---
<details>
<summary>TBD</summary>
</details>
---
<br>
## Stacking Classifier <a href="https://github.com/stgrmks/StackingClassifier" class="btn">![View on GitHub](/img/GitHub-Mark-32px.png "View on GitHub")</a>
---
<details>
<summary>Stacked generalization (or stacking) (Wolpert, 1992) is a different way of combining multiple models, that introduces the concept of a meta learner.</summary>
Although an attractive idea, it is less widely used than bagging and boosting. Unlike bagging and boosting, stacking may be (and normally is) used to combine models of different types. The procedure is as follows:<br><br>
<ol>
<li>Split the training set into disjoint N sets.</li>
<li>Train base learner on N-1 sets and predict on the left out set.</li>
<li>Repeat until all sets were left out once.</li>
<li>Either take average of all predictions or simply feed all predictions from 3) as input for another layer of base learners.</li>
<li>Repeat procedure for arbitrary levels.</li>
</ol>
</details>
---
<br>
## Master Thesis <a href="https://github.com/stgrmks/Master-thesis" class="btn">![View on GitHub](/img/GitHub-Mark-32px.png "View on GitHub")</a>
---
#### Title: Wearable Sensor based Human Activity Recognition with Recurrent Neural Networks
<details>
<summary><b>Abstract</b></summary>
This work is concerned with human activity recognition (HAR) based on signals recorded with wearable sensors. Traditional HAR approaches often require domain specific knowledge to generate handcrafted features, a feature selection strategy to identify the most informative ones and a supervised learning algorithm to solve the task. This thesis evaluates the practicability of recurrent neural networks (RNNs) for the HAR problem. RNN based models are well suited in theory, since they extract informative features from raw sensor data automatically, can be trained in a supervised fashion and are tailored to model temporal dynamics. The investigated architectures are based on long short-term memory (LSTM) and gated recurrent unit (GRU) networks, hybrid networks with convoluonal and recurrent layers and residual networks (ResNets) applied on recurrent layers. The performance of the networks is evaluated on three public and one private dataset, covering a diverse selection of activities and subjects. All datasets were subject to a train, validation and test split and a leave-one-subject-out-cross-validation (LOSOCV) evalution procedure. In order to have a valid comparison with the tradi onal HAR approach, a random forest (RF) classifier was trained on time and frequency domain features. Furthermore, a grid search was carried out for all models, based on a validation set, to find the best hyperparameters. Results show that the proposed networks outperform the traditional approach in both evaluation procedures on three out of four datasets and are competitive in the remaining one. This suggests that the time extensive process of generating handcrafted features based on domain specific knowledge can be avoided by relying on RNNs. However, any neural network (NN) based model requires careful hyperparameter op mization, which in turn is a very time consuming process with an uncertain prospect of success.
</details>
---
<br>

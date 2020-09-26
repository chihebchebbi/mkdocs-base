# **How to build a Machine Learning Intrusion Detection system**

## Introduction

Machine learning techniques are changing our view of the world and they are impacting all aspects of our daily life. Thus machine learning is playing a huge role in information security. In this module you will not only explore the fundamentals behind machine learning techniques but you will dive into a hands-on experience to learn how to build real world Intrusion detection systems from scratch using cutting edge techniques, programming libraries and publicly available datasets. 

This module will cover:

*	Machine learning models
*	The required steps to build a Machine learning project
*	How to evaluate a machine learning Model
*	Most useful Data Science and Machine learning libraries
*	Artificial Neural Networks and Deep Learning
*	Next Generation Intrusion detection systems using Machine learning Techniques. 


## Artificial intelligence  

Artificial intelligence is the art of making computer programs to behave like a human and by behave i mean perceiving, learning, understanding and knowing. AI is involving many areas such as computer science, neuroscience, psychology and so on. 

![](RackMultipart20200926-4-kmxakm_html_69942718d81c4342.jpg)

## Machine Learning models 

Machine learning is the study and the creation of algorithms that learn from given data and examples. It is a particular approach to artificial intelligence.Tom M. Mitchell (an american computer scientist ) defines machine learning as &quot;A computer program is said to learn from experience _E_ with respect to some class of tasks _T_ and performance measure _P_ if its performance at tasks in _T_, as measured by _P_, improves with experience _E_&quot; . In machine learning we have four major models; supervised, semi-supervised,unsupervised and reinforcement.

- **Supervised learning:**  if we have the Input and the Output variable then it is a supervised learning. In this case we only need to map the function between the inputs and the outputs. Supervised learning could be divided into two other sub-categories; Classification and regression:
  - **Classification: ** when the output is a categorical variable
  - **Regression:**  when the output variables are continuous values.

Let&#39;s discover some supervised learning algorithms:

- **Naive Bayes: ** this classification [algorithm](https://www.peerlyst.com/tags/algorithm) is based on the the Bayes&#39; theorem.

![](RackMultipart20200926-4-kmxakm_html_5fcc0af514b064d5.png)

- **Decision Trees:**  are machine learning algorithms that predict the possible outputs thanks to a tree-like graph,the entire data is represented as a [root](https://www.peerlyst.com/tags/root-1) node and the final leafs are called Terminal Nodes.Dividable nodes are known as Decision Nodes.
- **Support Vector Machines:**  are binary classifiers used to identify a separating hyper-plane of data that are represented in a multi-dimensional space.Thus, that hyper-plane is not necessary a simple line.

![](RackMultipart20200926-4-kmxakm_html_77ae3c301d44d0d8.gif)

- **Semi-supervised:**  this model is not fully supervised while it contains both labeled and unlabeled data. This model is used generally to improve the learning accuracy.
- **Unsupervised: ** If we don&#39;t have information about the output variables then it is unsupervised learning.The model is trained totally with unlabeled data.Clustering is one of the most well known unsupervised techniques.

![](RackMultipart20200926-4-kmxakm_html_bf051b4e6f277f60.jpg)

- **Reinforcement:**  in this model the agent is being optimized based on the feedback from the environment (the reward)

![](RackMultipart20200926-4-kmxakm_html_5ced71150a1c873a.png)

To learn how to choose the suitable Machine learning algorithm you can [download](https://www.peerlyst.com/tags/download) this useful sheet : [Machine Learning Algorithms sheet](https://static.peerlyst.com/image/upload/v1519069453/post-attachments/Machine_Learning_Algorithms_sheet_lirrpc.pdf)

**Machine learning steps**

In order to build a Machine learning model our project need to follow two major phases; training and experimenting. During the training phase a feature engineering operation is needed because it is critical to feed the machine learning model with a well defined features. Not all the data is useful in our project. After choosing the machine learning algorithm that we are going to use, we feed it by the chosen data. After training, we need to put the model into a test or what we call an experience to evaluate the model based on many evaluation metrics.

**Machine learning evaluation metrics**

Building a machine learning model is a methodological process. Thus, in order to test our machine learning model performance we need to use a well-defined metrics based on scientific formulas: all these formulas are needing four parameters; [false positive](https://www.peerlyst.com/tags/false-positive), true positive, false negative and true negative.

![](RackMultipart20200926-4-kmxakm_html_d2f210b13efbe5e.png)

Notation

- tp = True Positive
- fp = False Positive
- tn = True Negative
- fn = False Negative

**Precision **

Precision or Positive Predictive Value, is the ratio of the positive samples that are correctly classified by the the total number of positive classified samples.Simply it is the number of the found samples were correct hits. ![](RackMultipart20200926-4-kmxakm_html_f57a30dabb29d977.png)

**Recall**

Recall or True Positive Rate, is the ratio of true positive classifications by the total number of positive samples in the dataset. It represents how many of the true positives were found.

![](RackMultipart20200926-4-kmxakm_html_2a5c8ca979c8b33a.png)

**F-Score**

F-Score of F-Measure, is a measure that combines precision and recall in a one harmonic formula

**Accuracy**

Accuracy is the ratio of the total correctly classified samples by the total number of samples. This measure is not sufficient by itself,because it is used when we have equal number of classes.

![](RackMultipart20200926-4-kmxakm_html_202cb22ff9823bc1.png)

**Confusion Matrix**

Confusion matrix is is a table that is often used to describe the performance of a classification model.

**Machine learning python frameworks**

As a programming language we used [python](https://www.peerlyst.com/tags/python) for many reasons. First comparing to other languages it is more productive and flexible than Java and C++.According to thestateofai.com 78% of [developers](https://www.peerlyst.com/tags/developers) are using python in their Artificial intelligence projects that means a better [documentation](https://www.peerlyst.com/tags/documentation) and support from the [development](https://www.peerlyst.com/tags/development) community. Python is coming with external, easy and advanced machine learning packages in terms of run-time and complexity. The following are some of the most used Python libraries in Machine learning:

•  **SciPy**  : it is used for [mathematics](https://www.peerlyst.com/tags/mathematics) and engineering field in general

•  **NumPy**  : it is used to manipulate large multi-dimensional arrays and linear algebra

•  **MatplotLib**  : it provides great [data visualization](https://www.peerlyst.com/tags/data-visualization) capabilities including: Confusion Matrix,Hitmaps,linear plots

•  **Tensorflow**  : is an [open-source](https://www.peerlyst.com/tags/open-source-1) library for machine intelligence and numerical computation developed by Google Brain Team within Google&#39;s Machine Intelligence research organization .You can deploy computation to one or more CPUs and GPUs.

•  **Keras** : is an [open source](https://www.peerlyst.com/tags/open-source) neural [network](https://www.peerlyst.com/tags/network) library written in Python running on top of TensorFlow to ease the experimentation and the evaluation of the neural [networks](https://www.peerlyst.com/tags/networks) model.

•  **Theano** : is an open source neural network library written in Python running on top of TensorFlow to ease the experimentation and the evaluation of the neural networks model.

To install any Python library this command will do the [job](https://www.peerlyst.com/tags/job) : _pip install Package-Here_

The following graph illustrates a comparison between some machine learning [frameworks](https://www.peerlyst.com/tags/frameworks) made by [Favio Vázquez](https://becominghuman.ai/@favio.vazquezp?source=post_header_lockup) especially Deep learning frameworks

![](RackMultipart20200926-4-kmxakm_html_50540eba7fd17ccc.png)

Wait, but what is Deep Learning?

**Artificial Neural networks and Deep Learning:**

The main goal of Artificial neural networks is to mimic how the brain works.To have a better understanding let&#39;s explore how a human brain actually works.Human brain is a fascinated complex entity with many different regions to perform various tasks like listening, seeing, tasting and so on. If the human brain is using many regions to perform multiple tasks so logically every region act using a specific algorithm for example an algorithm for seeing, an algorithm for hearing etc...Right? Wrong! The brain is working using ONE Algorithm. This hypothesis It is called The &quot;one learning algorithm&quot; hypothesis. There is some evidence that the human brain uses essentially _the same algorithm_ to understand many different input modalities. For more information check Ferret experiments, in which the &quot;input&quot; for vision was plugged into auditory part of brain, and the auditory cortex learns to &quot;see.&quot; The cell that compose the neuron system is called a neuron.The information transmission is happening using electrochemical signalling and propagation is done thanks to the neuron dendrites.

![](RackMultipart20200926-4-kmxakm_html_d7bd6db465b739ef.jpg)

The analogy of the human brain neuron in machine learning is called a perceptron. All the input data is summed and the output applies an activation function. We can see activation functions as information gates.

![](RackMultipart20200926-4-kmxakm_html_70064f64d2a4962.png)

**PS:**  &quot; **The analogy between a perceptron and a human neuron is not totally correct. It is used just to give a glimpse about how a perceptron works. The human mind is so far more complicated than Artificial neural networks. There are few similarities but a comparison between the mind and Neural networks is not really correct.&quot;**

There are many used activation functions:

- **Step Function** : Every output node have a predefined threshold value
- **Sigmoid Function** : Sigmoid functions are one of the most widely used activation functions
- **Tanh Function** : Another activation function used is the Tanh function
- **ReLu Function** : It is also called a rectified linear unit.It gives an output x if x is positive and 0 otherwise.

![](RackMultipart20200926-4-kmxakm_html_60ce30c231b04cf.png)

Many connected perceptrons build a simple neural network that consists of three parts: Input layer,hidden layer and an output layer.The hidden layer is playing the inter-communication role in the neural network or sometimes what what we call a Multi-layer perceptron network. If we have more than 3 hidden layers then we are talking about Deep Learning and Deep learning Networks.

![](RackMultipart20200926-4-kmxakm_html_359d425d71651515.png)

According to the data scientist and deep learning experts like the machine learning practitioner Dr. Jason Brownlee; every deep learning model must go thru five steps:

•  **Network Definition:**  in this phase we need to define the layers.Thanks to Keras this step is easy because it defines neural networks as sequences and to define layers we just need to create a sequence instance with mentioning the number of outputs

•  **Network Compiling:**  Now we need to compile the network including choosing the optimizing technique like Stochastic Gradient Descent (sgd) and a Loss function (Loss function is used to measure the degree of fit) to evaluate the model we can use Mean Squared [Error](https://www.peerlyst.com/tags/error) (mse)

•  **Network Fitting:** a Back-Propagation algorithm is used during this step based on the parameters specified in the compiling step.

• **Network Evaluation :**  After fitting the network an evaluation operation is needed to evaluate the performance of the model

•  **Prediction: ** Finally after [training](https://www.peerlyst.com/tags/training) the [deep learning](https://www.peerlyst.com/tags/deep-learning)model we now can use it to predict a new [malware](https://www.peerlyst.com/tags/malware) sample using a [testing](https://www.peerlyst.com/tags/testing)dataset

**Intrusion detection systems with Machine learning**

Dangerous [hackers](https://www.peerlyst.com/tags/hackers) are inventing new techniques in a daily basis to bypass security layers and avoid detection.Thus it is time to figure out new techniques to defend against cyber threats. [Intrusion detection](https://www.peerlyst.com/tags/intrusion-detection) systems are a set of devices or pieces of software that play a huge role in modern organizations to defend against intrusions and [malicious](https://www.peerlyst.com/tags/malicious) activities.We have two major [intrusion](https://www.peerlyst.com/tags/intrusion) [detection](https://www.peerlyst.com/tags/detection) system categories:

- **Host Based Intrusion Detection Systems (HIDS): **they run on the enterprise hosts to
- **Network Based Intrusion Detection Systems (NIDS):** their role is to detect network anomalies by [monitoring](https://www.peerlyst.com/tags/monitoring) the inbound and outbound traffic.

The detection can be done using two intrusion detection techniques:

- **Signature based detection technique:**  the traffic is compared against a [database](https://www.peerlyst.com/tags/database) of [signatures](https://www.peerlyst.com/tags/signatures) of known [threats](https://www.peerlyst.com/tags/threats)
- Anomaly-based intrusion technique: inspects the traffic based on the behavior of activities.

![](RackMultipart20200926-4-kmxakm_html_6c37206948520baa.png)

Modern organization are facing thousands of threats in a daily basis.That is way the classic techniques could not be a wise solution to defend against them.Many [researchers](https://www.peerlyst.com/tags/researchers) and information [security professionals](https://www.peerlyst.com/tags/security-professionals) are coming with new concepts,prototypes or models to try solving this serious security issues.For example this is graph shows the different intrusion detection techniques including the discussed machine learning algorithms

![](RackMultipart20200926-4-kmxakm_html_f36bf154bfca569c.jpg)

By now, after reading the previous sections we are able to build a Machine learning detection system. As discussed before the first step is Data processing.The are many publicly available datasets in the wild used by data scientist to train machine learning models.You can download some of them from here:

- The ADFA Intrusion Detection Datasets:  [https://www.unsw.adfa.edu.au/australian-centre-for-cyber-security/cybersecurity/ADFA-IDS-Datasets/](https://www.unsw.adfa.edu.au/australian-centre-for-cyber-security/cybersecurity/ADFA-IDS-Datasets/)
- Publicly available [pcap](https://www.peerlyst.com/tags/pcap) files: [http://www.netresec.com/?page=PcapFiles](http://www.netresec.com/?page=PcapFiles)
- The Cyber Research Center - DataSets: [https://www.westpoint.edu/crc/SitePages/DataSets.aspx](https://www.westpoint.edu/crc/SitePages/DataSets.aspx)
- The NSL-KDD dataset: [https://github.com/defcom17/NSL\_KDD](https://github.com/defcom17/NSL_KDD)

The NSL-KDD is one of the most used datasets in intrusion detection anomaly based models.It contains different attacks categories: DoS, Probe, U2R and R2L.

It is an enhanced dataset from the KDD99 dataset

![](RackMultipart20200926-4-kmxakm_html_6db25479b452e33.png)

After choosing the feature that you are going to work on and splitting the dataset into two sub-datasets for the training and the experience (They should not be the same) you can choose one of the machine learning algorithms represented in the graph of intrusion detection techniques and train your model.Finally when you finish the training phase it is time to put your model to the test and check its accuracy based on the machine learning evaluation metrics. To explore some of the tested models i recommend taking an eye on &quot;Shallow and Deep Networks Intrusion Detection System: A [Taxonomy](https://www.peerlyst.com/tags/taxonomy) and Survey&quot; research paper.

There are a lot of talks about the promise of machine learning or [AI](https://www.peerlyst.com/tags/ai) in [information security](https://www.peerlyst.com/tags/information-security) but in the other side there is a debate and some concerns about it. To discover more about Machine learning promises in [cyber security](https://www.peerlyst.com/tags/cyber-security) it is highly recommended to watch  **Thomas Dullien**  Talk : &quot; **Machine Learning, offense, and the future of automation**&quot; from here: [Machine learning, offense, and the future of automation](https://www.peerlyst.com/posts/video-thomas-dullien-machine-learning-offense-and-the-future-of-automation-peerlyst)

You can also download the presentation slides from this link: [Presentation Slides](https://2017.zeronights.org/wp-content/uploads/materials/ZN17_Thomas_Dullien_Machine%20learning,%20offense,%20and%20the%20future%20of%20automation.pdf)

**Summary**

This article is a [fair](https://www.peerlyst.com/tags/fair) overview of machine learning in information security.We discussed the required fundamentals in every machine learning project starting from the fundamentals to gaining the skills to build a machine learning projects.We took intrusion detection systems as real world case study.




2 [https://www.slideshare.net/idsecconf/jim-geovedi-machine-learning-for-cybersecurity](https://www.slideshare.net/idsecconf/jim-geovedi-machine-learning-for-cybersecurity)

3  [https://blog.capterra.com/artificial-intelligence-in-cybersecurity/](https://blog.capterra.com/artificial-intelligence-in-cybersecurity/)

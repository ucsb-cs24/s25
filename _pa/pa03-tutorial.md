---
num: pa03-tutorial
ready: true
desc: "A Gentle Introduction to Graphs and Neural Networks"
---

{% include mathjax.html %}


### A Gentle Introduction to Neural Networks

This section will serve as a semi-thorough introductory explanation of neural networks for the brave and curious. 

You have previously learned about *specific types* of graphs liked linked lists and binary trees. The graph is the generic structure on which those data structures are realized: a collection of nodes and connections between them. All binary trees, for example, are graphs, but not all graphs are binary trees. 

We can understand this better by seeing which limitations the binary tree puts on the graph structure:
- There is a single "root" node which has no incoming connections. 
- Every node has at most two outgoing connections, collectively called "children"
- Every node, except the root, has exactly one incoming connection, called the "parent"
- A node may never have an outgoing connection to an ancestor or cousin.

###### The power of a Graph
Now, let's go back to talking about the generic graph structure. 

![NeuralNetwork Example](assets/generic_weighted_directed_graph.svg)

Take a moment to study this image, and understand the components of the structure. A good idea would be to think about how this generic graph is represented in code with an adjacency list. 

Graphs are powerful, in that they can represent and model many different kinds of situations and problems. Suppose we had the problem of finding the shortest path from one city to another. So, we might choose to let this graph represent a collection of cities (nodes) which connect to other nodes through connections (highways). Each connection might be "weighted" which could indicate the length of the highway. Finally, the directedness could indicate the valid route of traversal on the connection; for example, it is invalid to travel from node 5 to node 2, but it is valid to travel from node 2 to node 5. We could then run algorithms on this graph to find interesting information, like the shortest distance from one city to another and solve our problem.  

Notice that our interpretation of the graph directly stems from our original problem of wanting to find the shortest path. In the context of this problem, we need to model the environment in this way in order to solve it. It wouldn't work if we interpreted weighted connections as the amount of traffic on the road, since that doesn't give us a complete picture of how long it will take to traverse it. 

###### Modeling the problem of Machine Learning

The goal of any machine learning model is to fit a solution to a collection of data. In other words: we use pre-existing data in order to make predictions for new, unseen, data. There are a variety of algorithms and model types that work well for particular problems, but this lab focuses on neural networks because of its underlying graph structure. Usually, we are concerned with writing a program ```P``` which takes input ```x``` and outputs ```y```. In machine learning, we instead are concerned with writing algorithm ```A``` which takes as input ```x``` and ```y```, and outputs program ```P```. This program ```P``` can then be used to take new instances of input ```x``` and make predictions as output ```y```.

With this problem in mind, we can think of a way to interpret a graph structure to achieve what we want. One structure that uses this "learning" model is the human brain. We as humans take as input many experiences, and we learn from these experiences and adapt to changes. So, we can choose to loosely interpret our graph as a brain! Here, we choose nodes to represent neurons, and connections between them to represent synapses. 

###### Understanding the structure of a Vanilla Fully Connected Feed Forward Neural Network

Just as we did before with the Binary Tree structure, let's outline the specific limitations (and indeed, upgrades) the neural network puts on its underlying graph structure (skip if you already read this in the original writeup):

- The Neural Network consists of "layers" which collectively partition the graph's nodes. Every node is apart of a layer, and layers may not share the same node.
- There is at least one input layer and one output layer. Every other layer is a "hidden" layer.
- The layers are ordered such that the input layer is first, and the output layer is last, each hidden layer specifically has a predecessor layer and a successor layer. 
- Every node in one layer has an outgoing connection to every node in the successor layer. A node may never have an outgoing connection to a layer that is not in the successor layer. 
- Every node can be "activated" with an activation function, which transforms the value held within the node. 
- Nodes in the input layer may not have incoming connections. Nodes in the output layer may not have outgoing connections. 
- Every connection is weighted.
- Every node, except for nodes in the input layer contain a term called the "bias".
- Typically, all nodes of a layer share the same activation function. 

Here is a diagram which outlines this structure:
![NeuralNetwork Example](assets/generic_neural_net.svg)

##### Making Predictions
For a neural network, the collections of weights and biases serves as the model, or as explained earlier - the mechanism in which we make a prediction. We insert the input into each node of the input layer. This diagram takes in two inputs, since there are two nodes in the input layer, each node gets a different input. The value is then transformed by each weight as it "flows" to the next layer. Once it reaches the next layer, it again gets transformed by the bias and activation function - in that order. After this, the same process happens as it flows to the next layer. In this example, it flows until it has been transformed by the output layer, which leaves the value in a state we interpret as a prediction. 

Lets look at a specific example which shows how exactly the values are being transformed. 

1. Assume the node with id 1 contains the input value: $x_1$ and the node with id 2 contains the input value: $x_2$.
2. To compute the value for node 3: $h_1$, we first accumulate the weighted sum:
$$h_1 = x_1w_1 + x_2w_4$$
3. Next, we add the bias term:
$$h_1 = x_1w_1 + x_2w_4 + b_1$$
4. Finally, activate the node with the activation function for its layer: $ReLU$

$$h_1 = ReLU(x_1w_1 + x_2w_4 + b_1)$$

Using these steps, we can compute the value for every other node, including the output node, which will be our prediction. 
- $h_2 = ReLU(x_1w_2 + x_2w_5 + b_2)$
- $h_3 = ReLU(x_1w_3 + x_2w_6 + b_3)$
- $y_1 = sigmoid(v_3w_7 + v_4w_8 + v_5w_9 + b_4)$

The important thing to realize is that these weights and biases are what control the prediction.

##### Training the Neural Network to make good predictions
Usually, the neural network starts off with random weights and zeroed biases. You can intuitively see how random weights and zeroed biases cause random predictions. 

So, neural networks employ a combination of two concepts:
- Gradient Descent
- Back Propagation

When a neural network makes a prediction, there is a sense of "how bad" of a prediction it was. This measure of quality can be found with a "Loss" function. In otherwords, the Loss function gives the neural network penalties and therefore incentive to improve. 

###### Gradient Descent
Once the Loss function outputs a penalty, gradient descent tells us how to update every single weight and bias in order to make a better prediction. Note that it gives us updates to these weights and biases to make a **better** prediction, not the **best** prediction. Because of this, we usually make multiple training passes to keep getting a *better* set of weights and biases until we reach some accuracy threshold on a test dataset (unseen data). To be specific, think of it as a black box that calculates a ```delta``` term for each weight and bias, where ```delta``` is the amount to be subtracted from the original weight or bias value. 

###### Back Propagation
When gradient descent calculates the change in a particular weight or bias, this change depends on changes made to nodes that come later in the neural network. 

The "error", in other words, gets propagated back through the neural network.
In general, for any ```delta``` $d$, $d$ is in the form $f_1f_2$, where $f_1$ is a factor in the ```delta``` for weights and biases in the previous layer. 



Here is a nifty little gif that depicts these processes. You can see how the input flows through the graph, and how the nodes are activated, as well as how the error gets propagated backward. 
![Prediction and Backprop](assets/backprop.gif)

### External Resources

###### BFS and DFS
- GeeksForGeeks BFS: <https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/>
- GeeksForGeeks DFS: <https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/>

###### Gradient Descent
You are not required to understand the math behind gradient descent, but if you are interested, this is a great resource:
- StatQuest - Gradient Descent: <https://www.youtube.com/watch?v=sDv4f4s2SB8>

###### Neural Networks: Required videos to watch
Here are some great resources to help you out. I would say that statquest has great videos to understand the implementation of neural network structures, whereas 3blue1brown is more conceptual based:
- StatQuest - Neural Network Basics (great for understanding the prediction algorithm): <https://youtu.be/CqOfi41LfDw?si=8waS2U01uMWcpH2i>
- StatQuest - Back Propagation (great for understanding the contribute algorithm): <https://youtu.be/IN2XmBhILt4?si=bnDft-3T4DQ2iO9X>
- 3Blue1Brown - <https://youtu.be/aircAruvnKk?si=KZt2AsbD7URc58-L>



### Credits
This assignment was conceived and created by UCSB CS ULA, Zackary Glazewski in consultation with Diba Mirza for CS 24. Thanks to the UCSB CS24 teaching staff for reviewing and providing feedback: Torin Schlunk, Mehak Dhaliwal, Nawel Alioua, Joseph Ng, Shinda Huang, Xinlei Feng, Yaoyi Bai, Ally Chu, and Sanjana Shankar.

[CC BY-NC-SA 2.0](https://creativecommons.org/licenses/by-nc-sa/2.0/), Zackary Glazewski and Diba Mirza, Feb 2024.





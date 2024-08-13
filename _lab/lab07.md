---
num: lab07
ready: true
desc: "Application of graphs to machine learning"
assigned: 2024-08-12 9:00:00.00-8
due: 2024-08-21 23:59:59.00-8
---
{% include mathjax.html %}

### Lab Goals
This lab is designed to offer a real-life application of graphs for a very relevant field of computer science: machine learning, by implementing the underlying graph algorithms of a neural network. 

###### What this Lab IS NOT about
- You will **NOT** be expected to learn and understand the theoretical inner workings of a neural network. 

- You will **NOT** need to implement everything in the neural network - the heavy lifting is done for you.  

- You will **NOT** need to worry about the architecture and design of the neural network. 

###### What this Lab IS about
- Applying graph algorithms to a graph data structure.
- Learning and understanding the underlying graph structure of a neural network.
- Implementing the basic class methods. 

### Collaboration Policy
You may work on this programming assignment with a partner. Make sure you add both your names at the top of main.cpp along with your perm numbers. Partnering is highly encouraged: working in groups is a highly beneficial skill to have moving forward as well as in the industry.

### Academic Integrity
All work submitted for this programming assignment must be your own, or from your partner. 

### Tips
- Don't be intimidated by the nature of the lab: focus on what you know about graphs and class structure and apply your skills as necessary. The neural network is meant to expose you to upper-division concepts earlier on and hopefully excite you for future classes. 
- Start early and ask questions! It may take some time to understand what we are requiring you to do. This project is larger than normal. There is a lot of code involved, but try to focus on the subset of code you are required to implement. 
- **The purpose of this lab is to write algorithms to traverse graphs (Breadth-First and Depth-First) in an applied way. Please read the specifications closely to see which functions require which algorithm. We have done the heavy lifting for you in terms of the neural network implementation and abstracted the math away behind visit functions. So, your plan should be to write a BFT and DFT algorithm and decide where to place these visit functions within them. First and foremost, this is a Graph centered lab in the context of neural networks, not a neural network-centered lab.**


### Project Structure
The files you will work in are ```NeuralNetwork.cpp``` and ```Graph.cpp```.
```Graph.cpp/hpp``` contains the following classes:
- ```NodeInfo```: contains information of a node.
- ```Connection```: contains information about a connection between two nodes.
- ```Graph```: contains the base graph structure you learned about in class, using an adjacency list.

```NeuralNetwork.cpp/hpp``` contains the following class:
- ```NeuralNetwork```: Inherits the graph structure and exposes other neural network methods. 


Other important classes/files that are part of the project are:

- ```DataLoader``` contains an implementation for an object that contains a dataset and is used to send data into the neural network. 

- ```utility``` contains miscellaneous functions to aid the neural network. 



###### Graph Structure
This particular graph structure maintains an adjacency list. The adjacency list uses **integer identifiers** to refer to each NodeInfo object. So, there is a ```std::vector<NodeInfo> nodes``` member variable which maps an identifier to its corresponding NodeInfo. The adjacency list is of type: ```std::vector<std::unordered_map<int, Connection>>```, that is, a vector of hashmaps.

### NeuralNetwork Structure
This class inherits from the graph class. It means you can access graph members within the NeuralNetwork class. This is because a NeuralNetwork is a specific type of graph, much like how a binary tree is a type of graph.

A neural network is a specific type of graph, just like a binary tree is a type of graph. Here are the specifications of the neural network structure:

- The Neural Network consists of "layers" which collectively partition the graph's nodes. Every node is part of a layer, and layers may not share the same node. Layers are sequential.
- There is at least one input layer and one output layer. Every other layer is a "hidden" layer.
- The layers are ordered such that the input layer is first, and the output layer is last, each hidden layer specifically has a predecessor layer and a successor layer. 
- Every node in one layer has an outgoing connection to every node in the successor layer. A node may never have an outgoing connection to a layer not in the successor layer. 
- Every node can be "activated" with an activation function, which transforms the value held within the node. 
- Nodes in the input layer may not have incoming connections. Nodes in the output layer may not have outgoing connections. 
- Every connection is weighted.
- Every node, except for nodes in the input layer, contains a term called the "bias".

Here is a diagram which outlines the structure of a neural network with three layers:
![NeuralNetwork Example](assets/generic_neural_net.svg)

The purpose of a neural network is to find a pattern of some training dataset in order to make accurate predictions on new, unseen data. In the image above, each $w_i$ and $b_i$ represent something called a weight and bias, respectively.


## Step by Step Instructions
#### Step 0: Create a Git Repo and get the starter code
Refer to lab01 for instructions on how to set up a GitHub repository and pull the starter code for this lab. Here is the link for this lab’s starter code: <https://github.com/ucsb-cs24-w24/STARTER-lab07>

#### Step 1: Run the executable
Review the Makefile provided and look on top of each file to understand how the code is organized. If you are having trouble, take a look at this Makefile tutorial guide: <https://zackglazewski.github.io/UCSBCS24-MakefileIntroduction/>

We provided a simple test suite in ```test_neuralnet.cpp```. For now, running ```./test_neuralnet``` will fail, this is because some important functions have not been initialized yet. Once you implement steps 2 and 3, try playing around with ```main.cpp``` which will load and test the accuracy of a pretrained neural network model.

#### Step 2: Implement Getters and Setters
Your first step is implementing the getters and setters for the ```Graph``` and ```NeuralNetwork``` classes.

The following getters and setters need to be completed:
- ```void NeuralNetwork::eval()```
- ```void NeuralNetwork::train()```
- ```void NeuralNetwork::setLearningRate(double lr)```
- ```void NeuralNetwork::setInputNodeIds(std::vector<int> inputNodeIds)```
- ```void NeuralNetwork::setOutputNodeIds(std::vector<int> outputNodeIds)```
- ```std::vector<int> NeuralNetwork::getInputNodeIds() const```
- ```std::vector<int> NeuralNetwork::getOutputNodeIds() const```

Despite the name ```NeuralNetwork::eval()``` and ```NeuralNetwork::train()```, these functions actually work to set the ```evaluating``` member in ```NeuralNetwork```. When ```NeuralNetwork::eval``` is called, the neural network should be put in "evaluation mode", where ```evaluating``` is set to true. Likewise, when ```NeuralNetwork::train``` is called, the neural network should be put in "training mode", where ```evaluating``` is set to false. 


#### Step 3: Implement Graph methods
The next step is implementing some of the class methods for the ```Graph``` class.

Notice the function ```void Graph::resize(int size)```. Before adding or updating any part of the structure, ```resize``` must be called first. 

For example, calling ```resize(20)``` will initialize ```nodes``` to be a vector of size 20, where every element is a ```nullptr```. Likewise, ```adjacencyList``` will be a vector of 20 empty maps. When writing these functions, assume that resize **has already been called**: it happens in the NeuralNetwork's constructors. 

You will need to implement the following functions:

- ```void Graph::updateNode(int id, NodeInfo n)```
    - Allocates a NodeInfo object on the heap and updates it in ```nodes```. 

- ```NodeInfo* Graph::getNode(int id) const```
    - This method should return a pointer to the NodeInfo object at the index ```id```.

- ```void Graph::updateConnection(int v, int u, double w)```
    - This method takes in a source id: ```v```, a destination id: ```u``` and a weight ```w```. The input represents a weighted and directed edge in the graph (from v to u). Update the adjacency list to reflect this update. Connections do not need to be allocated on the heap. If the connection already exists, just update the weight.

- ```void Graph::clear()```
    - This method should deallocate any allocated memory from the heap.
 
One indication that you have implemented the functions so far correctly is that the test_structure test case `./test_neuralnet 4` should pass.


#### Step 4: Implement Predict with BFT
The next two steps will be the most challenging part of the programming assignment. We recommend taking the self-test assignment on Gradescope before implementing these functions.

You will need to implement a BFT (Breadth First Traversal) algorithm for:
- ```std::vector<double> predict(DataInstance instance)```

    - This function takes an input training example, ```instance```, and returns the neural network's prediction (a vector, in the case where a neural network is defined to have more than one output). 

To implement a BFT, you should not use the `NeuralNetwork::layers` member variable. Instead, implement it using a `queue` as stated in the starter code of the predict function.

A BFT is required for this function because of how input flows through a neural network, which will be discussed further down below. 

We have provided you two important functions that take care of the math for you:
- ```NeuralNetwork::visitPredictNode(int vId)```: 
    - takes care of the neural network math for visiting a node during the prediction phase. Computation will be performed on the NodeInfo whose id is ```vId```.

- ```NeuralNetwork::visitPredictNeighbor(Connection c)```: 
    - takes care of the neural network math for visiting a connection during the prediction phase. Computation will be performed on the nodes that make up the connection ```c```.

Your job is to write the BFT algorithm that visits nodes and connections in the right order.  

Here is a rundown of how the prediction algorithm works.

![NeuralNetwork Example](assets/generic_neural_net.svg){:width=25% }

For a neural network, the collections of weights and biases serve as the model or - the mechanism in which we make a prediction. We insert the input into each node of the input layer. This diagram takes in two inputs; since there are two nodes in the input layer, each node gets a different input. The value is then transformed by each weight as it "flows" to the next layer. Once it reaches the next layer, it again gets transformed by the bias and activation function - in that order. After this, the same process happens as it flows to the next layer. In this example, it flows until it has been transformed by the output layer, which leaves the value in a state we interpret as a prediction. For any given layer, we first visit all the nodes and connections to the next layer before visiting the nodes and connections of the next layer. Here is an example of how input flows from the input layer to the hidden layer in our example:

1. Assume the node with id 1 contains the input value $x_1$, and the node with id 2 contains the input value $x_2$.
2. To compute the value for node 3: $h_1$, we first accumulate the weighted sum:
$$h_1 = x_1w_1 + x_2w_4$$
3. Next, we add the bias term:
$$h_1 = x_1w_1 + x_2w_4 + b_1$$
4. Finally, activate the node with the activation function for its layer, which we will call ```activate```:

$$h_1 = activate(x_1w_1 + x_2w_4 + b_1)$$

Using these steps, we can compute the value for every other node, including the output node ($y_1$), which will be our prediction. 
- $h_2 = activate(x_1w_2 + x_2w_5 + b_2)$
- $h_3 = activate(x_1w_3 + x_2w_6 + b_3)$
- $y_1 = activate(h_1w_7 + h_2w_8 + h_3w_9 + b_4)$


**NOTE**: Keep these two facts in mind when writing your prediction algorithm.
- visiting a connection accumulates a part of the weighted sum.
    - for example: visiting the connection with $w_5$ is responsible for calculating the $x_2w_5$ term. 
- visiting a node adds the bias and activates.



The other important thing to realize is that a layer must wait for the computation of the previous layer to finish, hence the need for a BFT traversal.

#### Step 5: Implement Contribute with DFS

Your next task is to implement a DFT (Depth First Traversal) algorithm for:
- ```bool NeuralNetwork::contribute(double y, double p);```
    - This is the main, public version of this function. ```y``` is the ground truth label and ```p``` was the neural network's prediction. 
- ```double NeuralNetwork::contribute(int nodeId, const double& y, const double& p);```
    - This is the recursive helper function for the main contribute function. ```y``` and ```p``` remain the same throughout each call, ```nodeId``` indicates the node that is currently being visited. 

A DFT is required for this process because of how errors are "back-propagated" through the neural network.

When a neural network makes a prediction, there is a sense of "how bad" the prediction was. The neural network has a mechanism for finding this out, which we've abstracted behind the visit functions. Curious students are encouraged to check the info in the [Gentle Introduction to Neural Networks](EXTRA.md) tutorial that provides more details, but it is not required to understand this lab.

Changing our weights and biases causes a different prediction, and the question to be answered is: how do we change these weights and biases to make a better prediction? 

The error begins in the output layer. The output layer uses fancy math to figure out how much to change its weights and biases. Then, a part of that error is passed down to the previous layer, which performs the same procedure. This "back-propagation" continues until we reach the input layer and its weights are updated. 

Here is a helpful gif to illustrate both the prediction flow and back-propagation flow:

![Prediction and Backprop](assets/backprop.gif)

Why do we use DFT for back-propagation? There are a couple of reasons:
1. The error received in one layer depends on some new error that the next layer computes and passes down. The error a node receives from its out-neighbors is an "incoming contribution" and the error that a node passes down to its in-neighbors is its "outgoing contribution". 
2. The connections are only forward-directed; you cannot traverse backward in the network without the help of a recursive call. 


![NeuralNetwork Example](assets/generic_neural_net.svg)

Here is an example, referring back to our original neural network: suppose we are currently at node 3

1. Iterate through all your neighbors. For each neighbor:
    - get the neighbor's incoming contribution by recursively calling contribute on node 6.
    - Using that incoming contribution, visit the connection corresponding to that neighbor.
    - In this case, we visit the connection with weight $w_7$.

2. Visit node 3 and pass in your running outgoing contribution to be updated.

Now, an example using node 1:
1. Get contribution from node 3, and visit the connection with $w_1$.
2. Get contribution from node 4, and visit the connection with $w_2$.
3. Get contribution from node 5, and visit the connection with $w_3$.
4. Visit node 1 and pass in your running outgoing contribution to be updated.

We have provided you with two important functions that take care of the math for you:

- ```void visitContributeNode(int vId, double& outgoingContribution)```:
    - Updates outgoingContribution and computes the contribution of the nodes ```delta``` term.
- ```void visitContributeNeighbor(Connection& c, double& incomingContribution, double& outgoingContribution)```:
    - Updates outgoingContribution and computes the contribution to the connection's ```delta``` term.

Notice ```incomingContribution``` and ```outgoingContribution``` defined in the function. During your DFT, ```incomingContribution``` will represent what comes from the recursive result of calling ```contribute``` on a neighbor. ```outgoingContribution``` will be updated throughout the duration of the recursive call and, eventually, be returned - becoming the new ```incomingContribution``` for the previous layer. 

In place of a "found" set, there is a map called ```contributions```. This acts as a way to keep track of nodes that we have already visited, as well as store their previously computed contributions. 

Your job is to write the DFT algorithm that visits nodes and connections in the right order. 

When you are ready to proceed with this step, see the following section, which will give a brief background of back-propagation:

#### Step 6: Implement Update

After calling contribute, the update function assumes (precondition) that the ```delta``` of every node and connection has been accumulated. Now, each delta must be applied to every node's bias and every connection's weight.

Your goal in the update is to traverse the graph (in any way you want) to update every weight and bias. A single call to ```update``` affects every node and connection and reset the $delta$ values to zero.

For each update, follow these steps:
1. To update the bias: $bias_{new} = bias_{old} - (lr * delta)$
2. To update the weight: $weight_{new} = weight_{old} - (lr * delta)$
3. Reset the $delta$ values for each node and connection to zero.

where $lr$ is the learning rate (a member variable of NeuralNetwork), and controls how impactful we consider contributions to be. 

#### Step 7: Test and Submit
```test_neuralnet.cpp``` has been given as a brief way to check your neural network. Please test your code against this file and make sure you pass all the tests before trying to submit to gradescope. 

If you are having issues, it is helpful to run a debugger like gdb to make sure your code is following the logic described above. 

#### Step 8: Rest
Take a break! You've done well. 



### External Resources

###### Graphviz
The graph class overloads the << operator and outputs the graph in dot format. Copy the portion that looks like:
```digraph G {...} ```
and paste it [here](https://dreampuf.github.io/GraphvizOnline/#digraph%20G%20%7B%0A%0A%20%20subgraph%20cluster_0%20%7B%0A%20%20%20%20style%3Dfilled%3B%0A%20%20%20%20color%3Dlightgrey%3B%0A%20%20%20%20node%20%5Bstyle%3Dfilled%2Ccolor%3Dwhite%5D%3B%0A%20%20%20%20a0%20-%3E%20a1%20-%3E%20a2%20-%3E%20a3%3B%0A%20%20%20%20label%20%3D%20%22process%20%231%22%3B%0A%20%20%7D%0A%0A%20%20subgraph%20cluster_1%20%7B%0A%20%20%20%20node%20%5Bstyle%3Dfilled%5D%3B%0A%20%20%20%20b0%20-%3E%20b1%20-%3E%20b2%20-%3E%20b3%3B%0A%20%20%20%20label%20%3D%20%22process%20%232%22%3B%0A%20%20%20%20color%3Dblue%0A%20%20%7D%0A%20%20start%20-%3E%20a0%3B%0A%20%20start%20-%3E%20b0%3B%0A%20%20a1%20-%3E%20b3%3B%0A%20%20b2%20-%3E%20a3%3B%0A%20%20a3%20-%3E%20a0%3B%0A%20%20a3%20-%3E%20end%3B%0A%20%20b3%20-%3E%20end%3B%0A%0A%20%20start%20%5Bshape%3DMdiamond%5D%3B%0A%20%20end%20%5Bshape%3DMsquare%5D%3B%0A%7D) to visualize the graph: 

###### BFS and DFS
- GeeksForGeeks BFS: <https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/>
- GeeksForGeeks DFS: <https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/>

###### Neural Networks
Here are some great resources to help you out. I would say that statquest has great videos to understand the implementation of neural network structures, whereas 3blue1brown is more conceptual based:
- StatQuest - Neural Network Basics (great for understanding the prediction algorithm): <https://youtu.be/CqOfi41LfDw?si=8waS2U01uMWcpH2i>
- StatQuest - Back Propagation (great for understanding the contribute algorithm): <https://youtu.be/IN2XmBhILt4?si=bnDft-3T4DQ2iO9X>
- 3Blue1Brown - <https://youtu.be/aircAruvnKk?si=KZt2AsbD7URc58-L>

### Credits
This assignment was conceived and created by UCSB CS ULA, Zackary Glazewski in consultation with Diba Mirza for CS 24. Thanks to the UCSB CS24 teaching staff for reviewing and providing feedback: Torin Schlunk, Mehak Dhaliwal, Nawel Alioua, Joseph Ng, Shinda Huang, Xinlei Feng, Yaoyi Bai, Ally Chu, and Sanjana Shankar.

[CC BY-NC-SA 2.0](https://creativecommons.org/licenses/by-nc-sa/2.0/), Zackary Glazewski and Diba Mirza, Feb 2024.
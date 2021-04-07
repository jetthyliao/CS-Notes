#Chapter 14

##D-Separation

Two variables A and B are d-separated iff for **every path** between them, there is an intermediate variable V such that either

- The connection is serial or diverging and V is known
- The connection is converging and neither V nor any descendant is instantiated 

Path Types:

- Diverging: A <- V -> B
- Converging: A -> V <- B
- Forward: A -> V -> B
- Backward: A <- V <- B

D-separated = Independent

ex. If A and B are D-separated given evidence e, then

- P(A|e) = P(A|B,e)


##Bayesian Network

A Bayesian network is a directed graph in which each node is annotated with quantitative probability information. 

- Each node corresponds to a random variable, which may be discrete or continuous
- A set of directed links or arrows connect pairs of nodes. If there is an arrow from node X to node Y, X is said to be a parent of Y. The graph has no directed cycles (and hence is a directed acyclic graph, or DAG)
- Each node X~i~ has a conditional probability distribution P(X~i~ | Parents(X~i~)) that quantifies the effect of the parents on the node

Conditional distribution usually represented as a **conditional probability table** (CPT)

###Markov Blanket

Markov Blanket: parents + children + children's parents

Each node is conditionally independent of all other given its Markov Blanket (nodes outside of blanket are independent of the original node)

###Chain Rule

Probability of a node is the product of the possible probability of its parents

Can use this to keep chaining and finding the probability of all nodes

###Joint Distribution To Answer Queries

Blind Approach: sum all uninstantiated variables from the full joint. Express the joint distribution as a product of conditionals. (This is a fuck ton of products)

Interleave sums and products Approach: combine sum and product in a smart way

###Variable Elimination



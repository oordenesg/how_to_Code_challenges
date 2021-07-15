# how_to_Code_challenges
Learn how to solve the most common coding challenges

In This repository we will cover the theorical part of the most common coding challenges. 

## Concepts

### Nodes

What is a node? They are fundamental building blocks of many computer science data structure. They form the basis of queues, trees and much more. In general, a contain data and links to other nodes. Let's imagine a node that contains a piece of data (a number) and a link to another node. 

The data contained wihin a node can be a variety of types, depending on the language you're using. So nodes can have numbers, strings, arrays or nothing. Howevers one node can contain a link to other node. These links are sometimes called pointers since the "point" to another node. 

Normally, a node has more than one link. If one these links is null, so we can say that link reached the end of the particular node. 

Often, due to the data structure, nodes may only be linked to from a single other node. This makes it very important to consider how you modify or remove nodes from the data structure. If we remove a link to node, we could lost our application. This is called an orphaned node.

- Nodes contain data, which can be a variety of data types.
- Contain links to other nodes. If a node has no links or they are just null. You have reached the end of the path you were folling.
- Nodes can be orphaned if there are no existing link to them. 

#### Nodes in Python

We are going to use a basic node that contains data and one link to another. In python node's data will be specified when creating the node and immutable. Let's create a node in Python

```python
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node
```

Now we need methods to access the data and link within the node. To do this we will use two getters.

```python
def get_value(self):
    return self.value
  
def get_link_node(self):
    return self.link_node
```

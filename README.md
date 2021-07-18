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
class Node:
  def __init__(self, value, link_node=None):
    self.value = value
    self.link_node = link_node

  def get_value(self):
    return self.value
  
  def get_link_node(self):
    return self.link_node
```

In this proces we are only allowing the value of the node to be set upon craetion. However, we want to allow update the link of the code. To do this we can use a setter to modify the *self.link_node*

```python
  def set_link_node(self,link_node):
     self.link_node = link_node
```

Let's try to track some characters using python. First we need to add three nodes. 

```python
yacko = Node("likes to yak")
wacko = Node("has a penchant for hoarding snacks")
dot = Node("enjoys spending time in movie lots")
```

Now, let's give these nodes some responsabilities. Yacko can keep track of dot and dot can keep up with wacko. wacko can't keep track of anything though. Then ,create two new variables dots_data and wackos_data. Use them to get dot's value from yacko and get wacko's value from dot. Finally, print both variables.

```python
dot.set_link_node(wacko)
yacko.set_link_node(dot)

dots_data = yacko.get_link_node().get_value()
wackos_data = dot.get_link_node().get_value()

print(dots_data)
print(wackos_data)
```

A similar concept is **linked list**. This definition uses the same idea of nodes. As you might recall, each linked link is a sequential chain of nodes. So before we start building out the *linkedList* itself, we want to build up a *Node* class. Let's create an empty node class. Then define get_value() ad get_next_node() methods. These should return self.

```python
class Node:
  def __init__(self,value,next_node = None):
    self.value = value
    self.next_node = next_node
  
  def get_value(self):
    return self.value
  
  def get_next_node(self):
    return self.next_node
```

After this, define a set_next_node() method that takes self and next_mode as parameters. This method should allow us to update the link to the next node. Finally, outside the node class create an instance of node called my_node with a value of 44. Use get_value to print the value of my_node.

```python
class Node:
  def __init__(self,value,next_node = None):
    self.value = value
    self.next_node = next_node
  
  def get_value(self):
    return self.value
  
  def get_next_node(self):
    return self.next_node
    
  def set_next_node(self,next_node):
    self.next_node = next_node

my_node = Node(44)
print(my_node.get_value())
```


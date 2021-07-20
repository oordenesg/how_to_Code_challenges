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

After we've created the Node, we can star building the actual linked list. Depending on the end-use of the linked list, a variety of methods can be defined. For our use, we want to be able to:

- get the head node of the list (it's like peeking at the first item i line)
- add a new node to the beginning of the list.
- print out the list values in order
- remove a node that has a particular value

Using our previous example, let's crate a linked list. 

Define an init() method for the linkedList. This method should take value as an argument. Inside the init() method, set self.head_node equal to a new Node with value as its value. Then define get_head_node() method that helps us peek at the first node in the list.

```python
class LinkedList:
  def __init__(self, value=None):
    self.head_node = Node(value)
  
  def get_head_node(self):
    return self.head_node
``` 
Now define an insert_beginning() method which takes new_value as an argument. Inside this method instantiate  a node with new_value. Name this new_node. Now, link new_node to the existing head_node. Finally replace the current head_node with new_node.

After this, fefine a .stringify_list() method we can use to print out a string representation of a list’s nodes’ values.The method should traverse the list, beginning at the head node, and collect each node’s value in a string. Once the end of the list has been reached, the method should return the string.

```python
  def insert_beginning(self, new_value):
    new_node = Node(new_value)
    new_node.set_next_node(self.head_node)
    self.head_node = new_node
    
  def stringify_list(self):
    string_list = ""
    current_node = self.get_head_node()
    while current_node:
      if current_node.get_value() != None:
        string_list += str(current_node.get_value()) + "\n"
      current_node = current_node.get_next_node()
    return string_list
  
# Test your code by uncommenting the statements below 
ll = LinkedList(5)
ll.insert_beginning(70)
ll.insert_beginning(5675)
ll.insert_beginning(90)
print(ll.stringify_list())
```
The final use case we mentioned was the ability to remove a node with a particular value. This is slightly more complex, since a couple of special cases need to be handled. Consider the followin case:

**a -> b -> c**. If node b is removed from the list, the new list should be **a -> c**. In this case need to update the link within the a node to match what b was pointing to prior to removing it from the linked list.

Lucky for us, in Python, nodes which are not referenced will be removed for us automatically. If we take care of the references, b will be “removed” for us in a process called Garbage Collection.

```python
  def remove_node(self, value_to_remove):
    current_node = self.get_head_node()
    if current_node.get_value() == value_to_remove:
      self.head_node = current_node.get_next_node()
    else:
      while current_node:
        next_node = current_node.get_next_node()
        if next_node.get_value() == value_to_remove:
          current_node.set_next_node(next_node.get_next_node())
          current_node = None
        else:
          current_node = next_node
```


#### Doubly Linked Lists Introduction

A double linked list is comprised of series of nodes. This strucutre is quite similar to a singly linked list.  In this case, each node contains data and two links to the next and previous node in the list. The head node is the node at the beginning of the list and the tail node is the node at the end of the list. 

Common operations on a doubl linked list my include:

- Adding nodes to both ends of the list.
- Removing nodes from both ends of the list.
- Finding and removing a node from anywhere in the list.
- Traversing (or traveling through) the list.

If we compared this case with the previous one (Single linked list), adding an additional list is a little complicated.  When adding to the head of the doubly linked list, we first need to check if there is a current head to list. If there isn't then the list is empty, and we can simply make our new node both the head and tail of the list and set both pointers to null. 

- Set the current head’s previous pointer to our new head
- Set the new head’s next pointer to the current head
- Set the new head’s previous pointer to null

Similarly, there are two cases when adding a node to the tail of a doubly linked list. If the list is empty, then we make the new node the head and tail of the list and set the pointers to null. If the list is not empty, then we:

- Set the current tail’s next pointer to the new tail
- Set the new tail’s previous pointer to the current tail
- Set the new tail’s next pointer to null

When it comes to removing the head or tail from the list, this process is still a bit more complicated than the single linked list.

Removing the head involves updating the pointer at the beginning of the list. Similarly, removing the tail involves updating the pointer at the end of list. In the double linked list, it is also possible to remove a node from the middle of the list. Since that node is neither the head nor the tail of the list, there are two pointers that must be updated:

- We must set the removed node’s preceding node’s next pointer to its following node
- We must set the removed node’s following node’s previous pointer to its preceding 

Now that we've learned about doubly linked list, lest's see an example using Python. We are going to use a provided Node class, which you can find at the top of script.py. We’ve added a prev_node property to the class, as well as .set_prev_node() and .get_prev_node() methods. Then in our DoublyLinkedList class at the bottom of script.py, create an __init__() method (constructor) that only has self as a parameter, since each list will be empty when it’s created. Inside your __init__() method create head_node and tail_node instance variables. The nodes have no value yet, so set them to None.

```python
class Node:
  def __init__(self, value, next_node=None, prev_node=None):
    self.value = value
    self.next_node = next_node
    self.prev_node = prev_node
    
  def set_next_node(self, next_node):
    self.next_node = next_node
    
  def get_next_node(self):
    return self.next_node

  def set_prev_node(self, prev_node):
    self.prev_node = prev_node
    
  def get_prev_node(self):
    return self.prev_node
  
  def get_value(self):
    return self.value
    

class DoublyLinkedList:
  def __init__(self):
    self.head_node = None
    self.tail_node = None
```


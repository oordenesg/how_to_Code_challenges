# How to Code Challenges
Learn how to solve the most common coding challenges

In This repository we will cover the theorical part of the most common coding challenges. 

Normally, juniors and senior developers must pass a technical interview to be hired. These interviews evaluate their ability to write. Technical interviews take many forms:

- Writing code alongside an employee of the company.
- testing online with a third-party service.
- Take-home challenges spanning several days.

## Technical Interviews: White Boarding 

A whiteboarding technical interview requires to plan and code the solution by hand. Candidates must comunicate their ideas or code without the assitance of a text editor or web browser.

The steps to pass a white boarding interview are:
1. Clarify the problem.
2. Create inputs.
3. Outline the solution.
4. Code the solution.
5. Test the solution.
6. Analyze the solution.

Let's check these steps in more detail.

#### 1. Clarify the problem

In this step, the interviewee must be confident they understand the dimension of the problem. In the software development world, ambiguity is one most common things. Even when the need is clear, a feature could have dozens of possible implementations. The key of this step is to repeat the question back to the interviewer in your own words. This gives you a momento to think about the problem and clarify your own ideas. In this step it is also important ask every clarifying question that comes to mind.

#### 2. Create inputs.

When the question is clear, we can start to create concrete inputs and outputs. You may staill be unclear how to solve the problem in code but we know that given an input *X*, our function should return an output *Y*. For example: Let's write a function which capitalizes the first letter of an input string. The first input could be 'apple' and our function should return 'Apple'. On the other hand, if our input is 'Apple' our function should return 'Apple'. Now, it is important to think about *edge cases* or inputs which do not reflect a commmon sceneario. What could happen if our input is *null*. These kind of scenarios are *edge cases*. 

#### 3. Outline the solution.

Now it is time to break down the problem by category. In this step we need to analyze different possibilities. Is this a searching question? Can we sort the input and will that help? Does this problem sound like it can be modeled as a graph, with vertices and connected edges?. In this case it is importan to understand the application of different data structures. In this step, the interviewer may make suggestion on how to proceed. After a couple of recommendations and when you and the interviewer are satisfied with a possible solucion, write the steps next to your input. Then, follow these steps as you arite code on the board. 

#### 4. Code the solution.

Now, it is time to write our solution. This is collaborative process. Refer to your outline and explain the step you're implementing.  In this step, try to avoid writing the code in silence or narrating at low level. When you're finished with the implementation, look it over for any mistake syntax or logical errors. 

#### 5. Test the solution.

Now use the test inputs to walk through the evaluation of your code. Here, you can write out any temporary variables on the board and update them when they change during execution. This is a good opportunity to showcase your communication. If during this process you catch an error, do not panic! Mistakes happen. This is the right time to explain the issue and talk through what you can do to fix the bug. 

#### 6. Analyze the solution.

You’re satisfied with your implementation and you’ve demonstrated how it works, but you’re not quite done. Analyze the time and space complexity of the solution. With this step you are demonstrating that you care about the efficiency of your code. Explain your code’s big O notation. If you can optimize to a more efficient runtime, explain how that would work. If you can’t optimize, explain why it’s not possible.

## Technical interview problems in Python

### List

List are fundamental data type in Python. In general, projects use lists to store data in sequential order. In interviews, it is expect to face at least one questions that requires working with lists. The first problem, one the most common ones, is reate a list or move elements forward by a number of k spaces. As we saw previously, it is important to clarify some questions.

*Should I account for negatives inputs?* The rotation input will always be positive
*What if the rotation is greater than the list lenght?* Continue wrapping. The rotated list would be the same as the original when k is equal to the lenght.



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

In the previous sceneario (single linked list), we can add to the head of the list by checking to see if it already has a head. We then either set the new node as the head or update the head property, and link the past head to the new head.This situation is a bit different in a double linked list. This is because we have an additional tail property and is built with nodes that each have two pointers. Let's how implement this using our previous example.

Define an .add_to_head() method that takes self and new_value as parameters. Inside this method create A new_head Node that takes new_value as a parameter and a current_head Node that’s set to the list’s head.

If there is a current head to the list:
- Set current_head‘s previous node to new_head
- Set new_head‘s next node to current_head

In this part, it is important to remember to use the Node class’s .set_prev_node() and .set_next_node() methods. After this, and outside of the if statement, set the list’s head to new_head. Finally, if the list doesn’t have a tail, set the list’s tail to the new head.

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

  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node == None:
      self.tail_node = new_head
```

Now its time to add the tail. Remember that doubly linked list have a tail property. Given this, we don’t have to iterate through the entire list to add to the tail like we did with a singly linked list. The new method will mirror what we did in our .add_to_head() method:

- Start by checking to see if there is a current tail to the list
- If there is (meaning the list is not empty), then we want to reset the pointers at the tail of the list: Set the current tail’s next node to the new tail and set the new tail’s previous node to the current tail
- Update the tail property to be the new tail
- Finally, if there isn’t a current head to the list (meaning the list was empty): Update the head property to be the new tail since that node will be both the head and tail

In order to see this process, let's define an .add_to_tail() method that takes self and new_value as parameters. Inside this method, create a new_tail Node that takes new_value as a parameter and a current_tail Node that’s set to the list’s tail.  Then if there is a current tail to the list, set the current tail’s next node to new_tail and set new_tail‘s previous node to the current tail. Then, outside your if statement, set the list’s tail to the new_tail and finally if the list doesn’t have a head, set the list’s head to the new tail.

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
  
  def add_to_head(self, new_value):
    new_head = Node(new_value)
    current_head = self.head_node

    if current_head != None:
      current_head.set_prev_node(new_head)
      new_head.set_next_node(current_head)

    self.head_node = new_head

    if self.tail_node == None:
      self.tail_node = new_head

  def add_to_tail(self, new_value):
    new_tail = Node(new_value)
    current_tail = self.tail_node

    if current_tail != None:
      current_tail.set_next_node(new_tail)
      new_tail.set_prev_node(current_tail)

    self.tail_node = new_tail

```

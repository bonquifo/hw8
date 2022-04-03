# hw8
In this homework assignment, you will implement the Dictionary ADT (part of the
PostScript interpreter) using a binary search tree (BST) data structure. A BST permits
an efficient lookup mechanism (as opposed to linear search) so there is an efficiency test to
ensure your code can handle a million entries.

The BST data structure

Please read section 9.5 in the textbook for a description of the binary search tree data struc-
ture. Alternatively, there are many web-pages/lecture notes on BST, the wiki page maybe
a good starting point (https://en.wikipedia.org/wiki/Binary search tree). In the textbook
(as well as some online sources), a separate BTNode class is used; we will not do that. Use a
nested node class as before.
Linked lists and arrays support insertion, removal or finding an entry in time proportional
to the number of entries in the container. Trees, on the other hand, offer a significant
efficiency advantage in that they generally support these operations in time proportional to
the log of the number of entries (assuming the tree is kept balanced).
In order to achieve the potential time efficiency of binary search trees, one needs to keep
the tree roughly balanced. In CompSci 535, you will learn some of the techniques used to do
this (as it happens, the tree-based containers in Java’s libraries use “red-black” trees). But
in this course, we will ignore the problems of unbalanced trees. Do not make any attempt
to re-balance your tree. The efficiency tests we run will make sure to construct a balanced
tree.

The Dictionary ADT represents a [lexicographically] sorted mapping of “names” to arbitrary
objects. It is used in the PostScript interpreter to hold definitions of procedures (among other
things). So, for example, it includes a mapping from the name ] to the _arrayEnd static
method that you wrote in Homework #7. For Homework #7, we used Java’s built-in HashMap
class. For this homework, you will re-implement the class using our own implementation. Of
course, in the “real world,” there would be no point to do this since using the library saves
a lot of work, but in this course, we want to have students learn how these library classes
work.
The Dictionary ADT supports the following public operations:
int size() Return number of entries in the dictionary.
boolean known(Name) Return whether the name has an entry in the dictionary.

Object get(Name) Return the value for the given name or throw an ExecutionException.
void put(Name,Object) Add (or replace) an entry for the given name. Throw ExecutionException
if the name is null.
int copy(Dictionary) Add all the entries from the argument (which must not be null)
to this dictionary.
Collection<Object> values() Return a collection of all the values of names in the
dictionary, in order.
String toString() Return a string of the form << name1 value1 ...namenvaluen>>
(notice that there are no punctuation characters, but everything inside is separated
by single spaces.). Also when names are printed, they have a prefixed with /, as in
/Bread.

We omit “remove” and iterator functionality from the ADT for simplicity. N.B., the dictio-
nary is not allowed to have two mappings for the same name; if “put” happens again for
the same name, the old entry is replaced.
The efficiency tests check to see that you built the tree correctly. If you wrote the code
efficiently, this test shouldn’t take more than 15 seconds or so. If you wrote the inefficient
(but easy) technique, the test will take much longer and you will lose points.

WHAT YOU NEED TO DO


First, you will need to implement the private recursive helper function (checkTree) that
checks if a subtree tree is well-formed, and if so returns how many nodes it has. Next, you
need to implement all the public methods for the Dictionary class using efficient binary
search tree algorithms. You may wish also to define other private (recursive) helper functions.
Our solution uses several.
As well as the four test suites (for internals, regular ADT operation, random testing, and
efficiency), you can also test the PostScript interpreter by running Main.

---
layout: post
title:  "To Newbs: Recursion is Useful"
categories: jekyll update python data-structures algorithms
---

# Recursion

I've often heard new programmers ask why recursion is so useful. My brother, a successful IOS developer still doesn't see the value in recursion (at least I gather from our conversations).

So, is recursion some pointless 'book' knowledge without practical use?

Not at all!

## What is Recursion?

Recursion is a call of a function repeatedly (from within itself) until some condition (called a basecase) is met that can solve all of the previous function calls.

What does that mean?

You're searching an unknown solution space that gets smaller with each function call.

What does <i>that</i> mean!? See below.

### Recursion At Work &mdash; Binary Tree Traversal

Say you need to traverse this tree and add up all the values you traverse on the way to the smallest value.
```
            10
           /  \
          5    17
        /  \    \
       1    8    20
```
First we need to find the smallest value (hint: the smallest value is the value in the lowest left corner). For us humans, the ingenious products of billions of years of evolution, this takes just a glance.

Then we can easily sum up all the values above it: `1 + 5 + 10 = 16`.

But how can we make our stupid silicon minions figure it out? There are multiple ways, but the most eloquent (and least amount of code) requires...

Recursion!

So, first things first, with any problem, we start with...

### The Algorithm

How would we traverse the tree in plain english? Well, we'd start at the top, at `10`, (also called the root node) and since it is a binary search tree (BST) we know that every value to the left of the current node is a smaller value and to the right a larger value.

So, starting at the root we'd do something like this:
    1. Does this node have a child to the left?
    2. If yes, go to that node and repeat the previous question
    3. If no, add up all the previous nodes and return the sum

### The Code
``` python
# Create our data type...
class Node:
    def init(self, value):
        self.value = value
        self.left = self.right = None

    def hasChildren(self):
        return self.left or self.right

    def isMinimum(self):
        return not hasChildren

# Create the tree...
tree = Node(10)
tree.left = Node(5)
tree.left.left = Node(1)
tree.right = Node(17)
tree.right.right = Node(20)

# Our recursive problem...
def sumNodesOnPathToMinimum(root):
    node = root
    # if no children we must be at the minimum value (or some other leaf node)
    if node.isMinimum:
        return node.value
    else:
        sumNodesOnPathToMinimum(node.left) + node.value
        # See what just happened? We used 'memory' by saying hey, we don't know what the sum is yet, but we know this value is going to be part of it, so let's save it here and ask the next node if it is the minimum. If it is, we will go back through the chain of function calls and make the final computation.

        # The final call would look something like:
        # root.value + node.left.value + node.left.left.value... and so on until we reach the minimum.

        # This is nice because: it is extremely simple and it is computationally efficient.

        # Think about how you would do this with a loop. It'd be quite a bit more clumsy, I think you'll agree.
```

Anything that has a basecase, or a continue-until-we-reach-the-end condition, is a great use of recursion. The solution to the base case ripples through all the callbacks on the stack until we get to the top call, which aggregates all the calls together.

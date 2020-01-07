# Search Graph Nodes \(Lintcode\)

## Question:

Given a `undirected graph`, a `node` and a `target`, return the nearest node to given node which value of it is target, return `NULL` if you can't find.

There is a `mapping` store the nodes' values in the given parameters.

 **Notice**

It's guaranteed there is only one available solutionHave you met this question in a real interview? Yes**Example**

```text
2------3  5
 \     |  | 
  \    |  |
   \   |  |
    \  |  |
      1 --4
Give a node 1, target is 50

there a hash named values which is [3,4,10,50,50], represent:
Value of node 1 is 3
Value of node 2 is 4
Value of node 3 is 10
Value of node 4 is 50
Value of node 5 is 50
```

## Thought:

* BFS
* No need to traverse by layer \(if you want all yes\)

## Solution:

```text
class Node()
    def __init__(self, val, neighbors):
        self.val = val
        self.neighbors = neighbors

class Solution():
    def searchNode(self, node, target):
        dq = collections.deque(node)
        nodes_set = set(node)
        while dq:
            curr = dq.popleft()
            if curr.val == target:
                return curr
            for neighbor in curr.neighbors:
                if neighbor not in nodes_set:
                    nodes_set.add(neighbor)
                    dq.append(neighbor)
        return None
        
```


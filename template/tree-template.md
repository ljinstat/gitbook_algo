# tree template

1. divide and conquer
2. DFS recursion

```text
def main():
	if not root:
		return
	self.sub_def(a, b, result)
	return result

def sub_def(self, a, b, result):
	if node:
		self.sub_def(node.left, result)
		self.sub_def(node.right, result)
```

3. BFS queue

```text
def bfs(root):
	if not root:
		return 
	dq = collections.deque()
	dq.append([root, 1])
	while dq:
		level, curr = dq.popleft()
		# result.append(curr.val)
		if not curr.left or not curr.right or not dq:
			return level
		if curr.left:
			dq.append([curr.left, level+1])
		if curr.right:
			dq.append([curr.rught, level+1])
```

## Valid Tree

1. DFS must have a recursion helper which call itself

```text
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        # ----use sub_def in main
        return self.dfs(root.left, root.right)
    
    def dfs(self, left, right):
    	# ----condition
        if not left and not right:
            return True
        if not left or not right:
            return False
        if left.val != right.val:
            return False
        # ----recursion of sub_def
        return self.dfs(left.left, right.right) and self.dfs(left.right, right.left)
```

2. BFS

```text
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        # ----initiation of queue
        dq = collections.deque([(root.left, root.right), ])
        while dq:
        	# pop elements
            left, right = dq.popleft()
            # conditions
            if not left and not right:
                continue
            if not left or not right:
                return False
            if left.val != right.val:
                return False
            # add new elements to the queue
            dq.append((left.right, right.left))
            dq.append((left.left, right.right))
        return True
```


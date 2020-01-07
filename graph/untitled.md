# 207. Course Schedule \(medium\) BFS

## Question:

There are a total of n courses you have to take, labeled from `0` to `n-1`.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: `[0,1]`

Given the total number of courses and a list of prerequisite **pairs**, is it possible for you to finish all courses?

**Example 1:**

```text
Input: 2, [[1,0]] 
Output: true
Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0. So it is possible.
```

## Thought:

* BFS and DFS
* build adjacent list and indegree dict
* visit all courses for once
* This problem is equivalent to finding if a cycle exists in a directed graph. If a cycle exists, no topological ordering exists and therefore it will be impossible to take all courses.
* DFS: check if the node is being visited, if it is true, there exists a cycle.

## Solution:

BFS

```text
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        edges = {i: [] for i in range(numCourses)}
        degrees = [0 for i in range(numCourses)] 
        for i, j in prerequisites:
            # direct graph
            edges[j].append(i)
            degrees[i] += 1
            
        queue, count = collections.deque([]), 0
        
        for i in range(numCourses):
            if degrees[i] == 0:
                queue.append(i)
        # BFS
        while queue:
            node = queue.popleft()
            count += 1
            for x in edges[node]:
                degrees[x] -= 1
                if degrees[x] == 0:
                    queue.append(x)

        return count == numCourses
```

DFS

```text
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        graph = {[] for _ in range(numCourses)}
        visited = [0 for _ in range(numCourses)]
        # create graph
        for pair in prerequisites:
            x, y = pair
            graph[x].append(y)
        # visit each node
        for i in range(numCourses):
            if not self.dfs(graph, visited, i):
                return False
        return True
    
    def dfs(self, graph, visited, i):
        # if ith node is marked as being visited, then a cycle is found
        if visited[i] == -1:
            return False
        # if it is done visted, then do not visit again
        if visited[i] == 1:
            return True
        # mark as being visited
        visited[i] = -1
        # visit all the neighbours
        for j in graph[i]:
            if not self.dfs(graph, visited, j):
                return False
        # after visit all the neighbours, mark it as done visited
        visited[i] = 1
        return True
```


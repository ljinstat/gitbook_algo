# 56. Merge Intervals \(medium\)

## Question:

Given a collection of intervals, merge all overlapping intervals.

```text
Input: [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```

## Thought:

* sort by the first element
* if **results is empty** or last interval in results does not share intersection with the current one, add current one
* else: maximum of the end of the current and the existing last one

## Solution:

```text
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return []
        results = []
        intervals.sort(key=lambda x: x[0])
        for i in intervals:
            if not results or results[-1][1] < i[0]:
                results.append(i)
            else:
                results[-1][1] = max(i[1], results[-1][1])
        return results
```


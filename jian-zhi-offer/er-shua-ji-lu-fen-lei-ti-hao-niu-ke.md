# 二刷记录（分类、题号、牛客）

\*\*\*\*[**题目分类**](https://blog.csdn.net/shi923281339/article/details/73604605)\*\*\*\*

**1. 数组：**

**3.1&3.2 数组中重复的数字**

**4. 二维数组的查找**

21：调整数组顺序使奇数位于偶数前面 **\(two pointers\)**

39：数组中出现次数超过一半的数字 **\(Boyer-moore voting algorithm\)**

42：连续子数组的最大和 **（divide and conquer/ dynamic programming）**

**12/8/19**

45：把数组排成最小的数 **\(sort\)**

49：丑数 **\(math: three sequences\) Non bug free**

50.1：字符串中第一个只出现一次的字符 **\(hash map\)**

50.2 删除字符串中所有重复出现的字符 **\(hash set\)**

50.3 判断两个单词是否互为变位词 **\(hash map, 26 letter count list, sort\)**

50（二）：字符流中第一个只出现一次的字符 **（hash map）**

_**51：**数组中的逆序对_ **\(merge sort\) \(unfinished\)**

**14/8/19**

56.1 数组中只出现一次的两个数字 **\(bit manipulation\) \(需要记忆，二刷基本忘记了\)**

_56.2 数组中唯一只出现一次的数字 \(_**bit manipulation\) 依然不懂**

57.1 和为s的两个数字 **\(two pointers\)**

57.2 和为s的连续正数序列 **\(two pointers\)**

_**59.2** 队列的最大值_ **\(应该是算queue里面吧，未完成\)**

61. 扑克牌的顺子 **\(hash table, heap sort, min sort\)**

63. 股票的最大利润 **\(两道，一道是通过记录最小价格和最大利润，另一道通过找到连续最小价格和连续最大价格\)**

**19/8/19**

7：重建二叉树 **\(preorder and inorder traversal, recursion\)**

8：二叉树的下一个结点 （**inorder traversal, divide and conquer**）

26：树的子结构 （**recursion: with another function, traverse left tree and right tree）**

27：二叉树的镜像 **\(recursion: top down and buttom up \(hard to explain\), BFS iteration\)**

28：对称的二叉树 **\(recursion: with another function, left and right nodes, BFS iteration: inside conditions are the same as recursion's\)**

32（二）：分行从上往下打印二叉树 **\(recursion: with another function, left and right nodes; BFS iteration: level nodes and level size\)**

32（一）：不分行从上往下打印二叉树 **（recursion: with another function, left and right nodes; BFS iteration）**

32（三）：之字形打印二叉树 **\(recursion: with another function, left and right nodes; BFS iteration: level nodes and level size\)**

33：二叉搜索树的后序遍历序列 **\(recursion: top down, left and right nodes\)**

33.2 二叉搜索树的先序遍历序列 **\(recursion: top down, left and right nodes\)**

**20/8/19**

34.1/ 2：二叉树中和为某一值的路径 **\(recursion: top down, left and right nodes; DFS+stack\)**

40：最小的k个数 **（max heap; partition; red and black tree）**

54. 二叉搜索树的第k大结点 （**inorder+recursion; iteration: DFS）**

55.1 二叉树的深度 **\(recursion: left and right; iteration: BFS+queue; DFS+stack\)**

68. ****树中两个结点的最低公共祖先 **\(binary search tree: iteration and recursion; binary tree: recursion\)**

36：_二叉搜索树与双向链表_ **（未完成）**

37：_序列化二叉树_ （未完成）

**21/8/19**

5. 替换空格 **（string; two pointers）**

**1**_**7：**打印1到最大的n位数_ \(还是有点搞不清楚\)

_**19**：正则表达式匹配 \(????\)_

_**20：**表示数值的字符串 \(hard???\)_

38：字符串的排列 **\(backtracking, recursion\)**

43：从1到n整数中1出现的次数 **\(math; hard\)**

**4**_**4：**数字序列中某一位的数字_ **\(math; hard\)**

45：把数组排成最小的数 **\(compare two strings, lambda, map, sorted\(key=comp\_to\_key\(\)\)\)**

58.1 翻转单词顺序**（先反转整个string，再挨个单词反转）**

58.2 左旋转字符串 **\(先各自反转两个部分，在把整个反转过string反转\)**

67. 把字符串转换成整数 **（考虑数值的正负，其他符号，加入数字怎么加）**

**23/8/19**

6：从尾到头打印链表 **\(stack, recursion\)**

18.1：删除链表节点 **\(O\(1\), 先copy下一个node的值到本node，再删除下一个，边界条件 （空，下一个为空，尾结点\)\)**

18.2: 删除链表中重复的结点 **\(the same as 18.1 but O\(1\)\)à**

22：链表中倒数第k个结点 **\(two pointers, one pass, 边界条件\)**

23：链表中环的入口结点 **（two pointers, math）**

24：反转链表 **（iteration: easier to understand; recursion）**

25：合并两个排序的链表 **\(iteration; recursion: the same as last one\)**

_35：复杂链表的复制_ \(138未完成\)

52：两个链表的第一个公共结点 **（stack；two passes 求长度；不用求长度，走完了自己的list**

**走别人的）**

**24/8/19**

10：斐波那契数列 **\(dynamic programming, memotization\)**

14：剪绳子 **\(重要**\) **\(memotization, greedy\)**

16：数值的整数次方 **\(recursion, edge cases\)**

_**17**：打印1到最大的n位数 ****_**\(string\)**

**25/8/19**

_**29：**顺时针打印矩阵_ **\(\)**

46：把数字翻译成字符串 **\(dynamic programming\)**

**27/8/19**

47：礼物的最大价值 **\(dynamic programming, 2D to 1D\)**

48：最长不含重复字符的子字符串 **\(sliding window, hashtable\)**

_**60:** n个骰子的点数_

**28/8/19**

66: 构建乘积数组 **\(math, iterative\)**

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*


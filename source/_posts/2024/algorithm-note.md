---
title: algorithm-note
date: 2024-04-24 19:05:19
tags:
---
# 算法笔记
## 前缀和
nums = [1, 2, 4, 3]
原地前缀和, 新的 nums[i] 表示 0 ~ i 的累计和
```
n = len(nums)
for i in range(1, n):
    nums[i] += nums[i - 1]
```
另外一种写法, 得到的 s 的长度为 n + 1, s[0] = 0
```
s = list(accumulate(nums, initial=0))
```
## 拓扑排序
```
from graphlib import TopologicalSorter
```
拓扑排序思想：
1、找到所有入度为 0 的节点存入双端队列
2、BFS，遍历到时入度减一，当入度为 0 时入队列
3、最终的 len(order) == 总的节点数，则表示排序成功，否则排序失败

模板
```
def topo_sort(self, edges):
    g = defaultdict(list)
    inDeg = defaultdict(int)
    for x, y in edges:
        inDeg[x] = 0

    for x, y in edges:
        g[x].append(y)
        inDeg[y] += 1

    q = deque([x for x, d in inDeg.items() if d == 0])
    
    order = []
    while q:
        x = q.popleft()
        order.append(x)
        for y in g[x]:
            inDeg[y] -= 1
            if inDeg[y] == 0:
                q.append(y)
    
    if len(order) == len(inDeg):
        return order
    else:
        return None
        
```
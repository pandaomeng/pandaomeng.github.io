---
title: 并查集 Python3 模板
date: 2024-03-18
tag: [algorithm, unionFind]
---

# 并查集模板
```
class UnionFind:
    def __init__(self):
        self.father = {}
        self.num_of_tree = 0
    
    def merge(self, x, y):
        x_root, y_root = self.find(x), self.find(y)
        if x_root != y_root:
            self.father[x_root] = y_root

    def find(self, x):
        root = x
        while self.father[root] != None:
            root = self.father[root]
        
        while x != root:
            origin_father = self.father[x]
            self.father[x] = root
            x = origin_father
        
        return root
    
    def add(self, x):
        if x not in self.father:
            self.father[x] = None

    def is_connected(self, x, y):
        return self.find(x) == self.find(y)
```




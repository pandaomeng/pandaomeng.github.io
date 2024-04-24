---
title: trie
date: 2024-04-24 12:22:06
tags: [trie]
---
# 前缀树模板
```
class Trie:
    def __init__(self):
        self.children = [None] * 26
        self.isEnd = False


    def insert(self, word: str) -> None:
        node = self
        for c in word:
            idx = ord(c) - ord('a')
            if not node.children[idx]:
                node.children[idx] = Trie()
            node = node.children[idx]
        node.isEnd = True
        

    def search(self, word: str) -> bool:
        node = self
        for c in word:
            idx = ord(c) - ord('a')
            if not node.children[idx]:
                return False
            else:
                node = node.children[idx]
        return node.isEnd


    def startsWith(self, prefix: str) -> bool:
        node = self
        for c in prefix:
            idx = ord(c) - ord('a')
            if not node.children[idx]:
                return False
            else:
                node = node.children[idx]
        return True
```
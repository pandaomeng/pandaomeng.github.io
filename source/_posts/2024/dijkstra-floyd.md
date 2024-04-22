---
title: dijkstra-floyd
date: 2024-04-22 11:59:49
tags: [dijkstra, floyd]
---

# dijkstra 模板

n 个节点，编号从 0 到 n-1
给定节点 start 和 end, 求最短路径

```
def dijkstra(edges, start, end):
    g = [[] for _ in range(n)]
    for x, y, w in edges:
        g[x].append((y, w))
        g[y].append((x, w))
    
    dist = [inf] * n
    dist[start] = 0
    h = [(0, start)]

    while h:
        dx, x = heappop(h)
        if dist[x] != dx:
            continue
        for y, w in g[x]:
            if dx + w < dist[y]:
                dist[y] = dx + w
                heappush(h, (dx + w, y))
    return dist[end] if dist[end] != inf else -1
```
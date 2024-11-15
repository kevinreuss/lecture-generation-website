# LRU and LFU Caching Algorithms

### LRU (Least Recently Used) Caching Algorithm

LRU works on the principle of "recency of use". The algorithm evicts the least recently used items first when the cache reaches its capacity. 

Here's a simple implementation in Python:

```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key) # update the 'recently used'-ness
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False) # remove least recent item
```

### LFU (Least Frequently Used) Caching Algorithm

LFU evicts the least frequently used items first. If two items have the same frequency, the least recently used item is evicted.

A Python implementation could look like this:

```python
import collections

class LFUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.key_node = {}
        self.freq_node = collections.defaultdict(collections.OrderedDict)
        self.min_freq = 0

    def get(self, key):
        if key not in self.key_node:
            return -1
        node = self.key_node[key]
        self.update(node)
        return node.val

    def put(self, key, value):
        if self.capacity == 0:
            return
        if key in self.key_node:
            node = self.key_node[key]
            self.update(node)
            node.val = value
        else:
            if len(self.key_node) == self.capacity:
                node = self.freq_node[self.min_freq].popitem(last=False)
                del self.key_node[node.key]
            node = Node(key, value)
            self.key_node[key] = node
            self.freq_node[1][key] = node
            self.min_freq = 1

    def update(self, node):
        freq = node.freq
        self.freq_node[freq].pop(node.key)
        if len(self.freq_node[freq]) == 0 and freq == self.min_freq:
            self.min_freq += 1
        node.freq += 1
        self.freq_node[node.freq][node.key] = node
```

Remember, both LRU and LFU have their strengths and weaknesses, and the choice between them depends largely on the specific requirements of your system.

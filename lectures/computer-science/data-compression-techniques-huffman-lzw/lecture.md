# Data Compression Techniques: Huffman, LZW

## Huffman Compression
Huffman coding is a lossless data compression algorithm. It creates variable-length prefix codes where frequent characters have shorter codes and infrequent characters have longer codes.
 
Here’s a simplified version of how it works:

1. Count the frequency of each character in the data.
2. Create a priority queue where each node contains a character and its frequency.
3. Dequeue the two nodes with the lowest frequencies and merge them into a single node with the combined frequency. The lower frequency node becomes the left child and the higher frequency node becomes the right child. Enqueue the new node.
4. Repeat step 3 until only one node remains in the queue. This node represents the root of the Huffman tree.
5. Assign binary codes to each character starting from the root. Moving to the left child adds a '0' and moving to the right child adds a '1'.

```python
# Python pseudo code for Huffman Coding
def build_huffman_tree(data):
    queue = PriorityQueue()
    for char, freq in count_frequency(data).items():
        queue.enqueue(Node(char, freq))
    while queue.size() > 1:
        node1 = queue.dequeue()
        node2 = queue.dequeue()
        merged = Node(None, node1.freq + node2.freq)
        merged.left = node1
        merged.right = node2
        queue.enqueue(merged)
    return queue.dequeue()  # return root of the tree
```

## Lempel-Ziv-Welch (LZW) Compression
LZW is a dictionary-based lossless data compression algorithm. It progressively builds a dictionary of phrases encountered in the input data, and emits the dictionary index of phrases instead of the phrases themselves.

Here’s how it works in a nutshell:

1. Initialize the dictionary to contain all single-character strings.
2. Read input symbols, grouping them into a string until the string is not in the dictionary.
3. Output the code for the longest prefix of the string that is in the dictionary.
4. Add the new string (longest prefix + next symbol) to the dictionary.
5. Start over at step 2 with the next symbol.

```python
# Python pseudo code for LZW Compression
def compress_lzw(data):
    dict_size = 256
    dictionary = {chr(i): i for i in range(dict_size)}
    string = ""
    compressed = []
    for symbol in data:
        string_plus_symbol = string + symbol
        if string_plus_symbol in dictionary:
            string = string_plus_symbol
        else:
            compressed.append(dictionary[string])
            dictionary[string_plus_symbol] = dict_size
            dict_size += 1
            string = symbol
    if string:
        compressed.append(dictionary[string])
    return compressed
```

Both Huffman and LZW offer efficient compression, but Huffman is better for data with clear frequency patterns, while LZW performs well on more diverse data.
# Huffman-Coding

## Aim
To implement Huffman Coding for data compression using Python programming.

---

## Software Required
- Anaconda – Python 3.7

---

## Algorithm

### Step 1
Get the input string from the user.

### Step 2
Calculate the frequency of occurrence of each character in the string.

### Step 3
Create tree nodes based on character frequencies.

### Step 4
Generate Huffman codes by constructing the Huffman tree.

### Step 5
Display the characters along with their corresponding Huffman codes.

---

# Program

## Get the Input String
```python
string = "BCAADDDCCACACAC"
```

## Create Tree Nodes
```python
class NodeTree(object):

    def __init__(self, left=None, right=None):

        self.left = left
        self.right = right

    def children(self):

        return (self.left, self.right)

    def nodes(self):

        return (self.left, self.right)

    def __str__(self):

        return '%s_%s' % (self.left, self.right)
```

## Main Function to Implement Huffman Coding
```python
def huffman_code_tree(node, left=True, binString=''):

    if type(node) is str:

        return {node: binString}

    (l, r) = node.children()

    d = dict()

    d.update(huffman_code_tree(l, True, binString + '0'))

    d.update(huffman_code_tree(r, False, binString + '1'))

    return d
```

## Calculate Frequency of Occurrence
```python
freq = {}

for c in string:

    if c in freq:

        freq[c] += 1

    else:

        freq[c] = 1

freq = sorted(freq.items(),
              key=lambda x: x[1],
              reverse=True)

nodes = freq

while len(nodes) > 1:

    (key1, c1) = nodes[-1]

    (key2, c2) = nodes[-2]

    nodes = nodes[:-2]

    node = NodeTree(key1, key2)

    nodes.append((node, c1 + c2))

    nodes = sorted(nodes,
                   key=lambda x: x[1],
                   reverse=True)
```

## Print the Characters and its Huffman Code
```python
huffmanCode = huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')

print('--------------------')

for (char, frequency) in freq:

    print(' %-4r | %12s' % (char, huffmanCode[char]))
```

---

# Output

## Print the Characters and its Huffman Code
```text
 Char | Huffman code
--------------------
 'C'  |          0
 'A'  |         10
 'D'  |        110
 'B'  |        111
```

---

# Result
Thus, Huffman Coding was successfully implemented to compress the data using Python programming.

---


# Languages Used
- Jupyter Notebook — 100.0%

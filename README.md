
# <p align="center">Huffman-Coding</p>

## Aim:
To implement Huffman coding to compress the data using Python.

## Software Required:
1. Anaconda - Python 3

## Algorithm:

### Step 1:
Get the input String.

### Step 2:
Create tree nodes.

### Step 3:
Main function to implement huffman coding.

### Step 4:
Calculate frequency of occurrence.

### Step 5:
Print the characters and its huffmancode.

## Program:
``` Python
#Developed by:Sanjay Kumar S S
#Register Number:212221240048  

# Create tree nodes
string = '212221240048 Sanjay Kumar'
class NodeTree(object):
    def __init__(self, left=None, right=None): 
        self.left = left
        self.right=right
    def children(self):
        return (self.left,self.right)
        
# Main function to implement huffman coding
def huffman_code_tree (node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree (l, True, binString + '0'))
    d.update(huffman_code_tree (r, False, binString + '1'))
    return d
    
# Calculate frequency of occurrence
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes=freq

while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)
    
# Print the characters and its huffmancode
huffmanCode=huffman_code_tree(nodes[0][0])
print(' Char | Huffman code ') 
print('----------------------')
for (char, frequency) in freq:
    print('%-4r|%12s'%(char,huffmanCode[char]))
```

## Output:
![image](https://github.com/SanjayKumarAIML/Huffman-Coding/assets/93427246/47137382-d987-4c4e-b4d8-67f552a1bd6e)
## Result:
Thus the huffman coding was implemented to compress the data using python programming.

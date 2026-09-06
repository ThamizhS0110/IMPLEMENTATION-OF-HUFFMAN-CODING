# IMPLEMENTATION-OF-HUFFMAN-CODING

## Name
Thamizh S

## Register Number
212224040350

## Objective

To implement the Huffman Coding algorithm for lossless data compression by generating variable-length binary codes based on the frequency of characters in an input string.

The techniques used are:

- Character frequency calculation
- Huffman tree construction
- Huffman code generation
- Lossless data compression

## Requirements

- Python 3
- Jupyter Notebook

## Methodology

1. Take the input string `thamizh`.
2. Calculate the frequency of each character in the input string.
3. Create tree nodes containing each character and its frequency.
4. Sort the nodes based on their frequencies.
5. Select the two nodes with the smallest frequencies.
6. Combine them to create a new node with the sum of their frequencies.
7. Repeat the process until a single Huffman tree is formed.
8. Traverse the Huffman tree to generate binary codes.
9. Assign `0` to the left branch and `1` to the right branch.
10. Display each character along with its corresponding Huffman code.

## Implementation

```python
# Step 1: Get the input string
input_string = "thamizh"

# Step 2: Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```
## output 
### Character | Huffman Code

<img width="257" height="173" alt="image" src="https://github.com/user-attachments/assets/c7c1cf54-8be9-4ed7-9694-4c0830cd52a2" />

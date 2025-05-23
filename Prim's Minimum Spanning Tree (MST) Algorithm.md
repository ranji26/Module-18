# Ex. No: 18A - Prim's Minimum Spanning Tree (MST) Algorithm

## AIM:
To write a Python program for **Prim's Minimum Spanning Tree (MST)** algorithm.

## ALGORITHM:

**Step 1**: Initialize the `key[]` array to infinity, set the first vertex's key to `0`, and create `mstSet[]` and `parent[]` arrays.

**Step 2**: Select the vertex with the smallest key value not yet included in `mstSet`.

**Step 3**: Add the selected vertex to `mstSet`.

**Step 4**: For all adjacent vertices:
- If the edge weight is smaller than their current key value, and the vertex is not in `mstSet`, then:
  - Update their key value
  - Update their parent to the current vertex

**Step 5**: Repeat Steps 2–4 until all vertices are included in the MST.

**Step 6**: Print the resulting Minimum Spanning Tree using the `parent[]` array.

## PYTHON PROGRAM

```

import sys # Library for INT_MAX
class Graph():
	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]
	def printMST(self, parent):
		print ("Edge   Weight")
		for i in range(1, self.V):
			print (parent[i], "-", i, "  ",self.graph[i][parent[i]])
	def minKey(self, key, mstSet):
		min = sys.maxsize
		for v in range(self.V):
			if key[v] < min and mstSet[v] == False:
				min = key[v]
				min_index = v
		return min_index
	def primMST(self):
		key = [sys.maxsize] * self.V
		parent = [None] * self.V # Array to store constructed MST
		key[0] = 0
		mstSet = [False] * self.V
		parent[0] = -1 
		for cout in range(self.V):
		    u=self.minKey(key,mstSet)
		    mstSet[u]=True
		    for v in range(self.V):
		        if self.graph[u][v]>0 and mstSet[v]==False and key[v]>self.graph[u][v]:
		            key[v]=self.graph[u][v]
		            parent[v]=u
		self.printMST(parent)
g = Graph(5)
g.graph = [ [0, 2, 0, 6, 0],
			[2, 0, 3, 8, 5],
			[0, 3, 0, 0, 7],
			[6, 8, 0, 0, 9],
			[0, 5, 7, 9, 0]]
g.primMST();
```

## OUTPUT

![image](https://github.com/user-attachments/assets/0a3c12a7-5387-4e4e-b24e-57a38e96262a)


## RESULT
Hence, The program is successfully executed and the Minimum Spanning Tree (MST) of the given connected, undirected, and weighted graph is obtained using Prim's algorithm.


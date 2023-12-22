# Data Structures w/Python



## Hash Maps


```python

#Simple hash map that does not factor in collision


class HashTable:
	def __init__(self):
		self.MAX = 100
		self.arr = [None for x in range(self.MAX)]
	get_hash = lambda self, key: sum([ord(char) for char in key]) % self.MAX

	def __setitem__(self, key, val):
		h = self.get_hash(key)
		self.arr[h] = val

	def __getitem__(self, key):
		h = self.get_hash(key)
		return self.arr[h]

	def __del__(self, key):
		h = self.get_hash(key)
		self.arr[h] = None

# A hashmap that does factor in collision

class HashTable:
	def __init__(self):
		self.MAX = 100
		self.arr = [[] for x in range(self.MAX)]
	get_hash = lambda self, key: sum([ord(char) for char in key]) % self.MAX

	def __setitem__(self, key, val):
		h = self.get_hash(key)
		if self.arr[h]:
			for i, thing in enumerate(self.arr[h]):
				if key == self.arr[h][i][0]:
					self.arr[h][i] = ()
					self.arr[h][i] += key, val
					return
		self.arr[h].append((key, val))

	def __getitem__(self, key):
		h = self.get_hash(key)
		item = None
		if self.arr[h]:
			for i, thing in enumerate(self.arr[h]):
				if self.arr[h][i][0] == key:
					item = self.arr[h][i][1]
		else:
			return f'{key} does not exist in the table, maybe you should make it?'
		return item

	def __delitem__(self, key):
		h = self.get_hash(key)
		if self.arr[h]:
			for i, thing in enumerate(self.arr[h]):
				if self.arr[h][i][0] == key:
					del self.arr[h][i]

```




```python


#THIS IS SIMPLY A PRACTICE FILE FOR MESSING AROUD WITH BFS
graph = {'5':['3', '7'],
        '3':['2', '4'],
        '7':['8'],
        '2':[],
        '4':['8'],
         '8':[]}
visited = []
queue = []
def bfs(visited, graph, node):
    visited.append(node)
    queue.append(node)
    while queue:
        m = queue.pop(0)
        print(f'{m} ')

        for neighbor in graph[m]:
            if neighbor not in visited:
                visited.append(neighbor)
                queue.append(neighbor)
#Call the function
bfs(visited, graph, '5')
#Ok so lest rewrite this and dissect what is going on.
''' Based on what I see in the code. A bfs starts from the first or oldes thing in a list. So whatever is at the top of the stack.
    So what do you need to make the thing work.
    1. You need a graph starting out. In this case we have a dictionary which has a key value pair of key=TheNode and Value=TheNodesChildren
    or paths.
        #NOTE# The main idea here is that we have an element that is linked to these other elements in some way.
                However you plan on achieving this doesnt really matter but the way you access those elements 
                are, then obviously, going to change depending on how you want to have, possibly, multiple elements
                associated with one element.
    2. You need a function that takes a minimum of 2 arguments, the graph as well as the Node you want to start the search 
    from.
        #NOTE# Remember the graph that you are passing to the function doesnt have to be an actual graph data structure.
                It would be a fun exercize to make a function that can handle a graph data structure and not just
                a dictionary.
    3. You need to consider how you want to store the visited elements and the elements that will be in the queue.
        Do you want to store them outside of the function, inside or maybe as additional keyword arguments in the function definition.
        #NOTE# Lets back up a little. Ok so why do we even need a container for visited elements and a container for elements to go
                into a queue?
                '''
graph = {'5':['3', '7'],
        '3':['2', '4'],
        '7':['8'],
        '2':[],
        '4':['8'],
         '8':[]}
def bfs(graph, node, visited=[], queue=[]):
    if node in graph:
        if graph[node]:
            for n in graph[node]:
                if n not in visited:
                    visited.append(n)
                    queue.append(n)
        if queue:
            print(queue[0])
            return bfs(graph, queue.pop(0), visited, queue)


```
## Depth First Search Practice

```python


''' Simple DFS practice and reminders'''
#So in this example im going to modify a doods tutorial to imrove it.
##Doo starts  with a dictionary which he calls the adjacency list which keeps track of all of the adjacent graph nodes.
adj_list = {'A':['C','B'], 'B':['D'], 'C': [], 'D': ['A','E']}

#Then he creates a couple more dictionaries in order to keep track of the nodes colors to determine if they have been visited or not
#and the second dictionary which is supposed to keep track of the parents for each given node.

color = {}
parent = {}

#Then he iterates through the adj_list with a for loop in order to populate the color and parent dictionary.
for node in adj_list:
    color[node] = 'WHITE'
    parent[node] = None
#Then he makes a dfs function
def dfs(node, color, parent):
    color[node] = 'GRAY'
    #Here he loops through the keys in the adjacency list:
    for vode in adj_list[node]:
        if color[vode] == 'WHITE':
            dfs(vode, color, parent)
        elif color[vode] == 'GRAY':
            print(f'CYCLE FOUND {node} to {vode}')
    color[node] = 'BLACK'
#Then outside of the function he uses a loop to send all of the adjacency keys in the dfs function iteravely
for node in adj_list:
    if color[node] = 'W':
        dfs(node, color, parent)

''' So the idea behind all this is that the dfs function is first supposed to print out the graph node by node along with each nodes adjacent nodes so paths that you could
get to from that node basically. So a node is printed out, then all of its adjacent nodes and then all of those nodes adjacent nodes and so on...
another thing we need to accomplish here is to be able to find if there is a cycle among these nodes, meaning is there a circular path of some sort so can we start off at a given
node and then end up at that same node after traversing through specifc nodes. If this is the case then we need to have the algorithm output this for us so we know.'''
#Ok so first off, I dont like this whole idea of all these different dicitonaries and for loops, two outside of the function and one inside. I feel like I can tackle this
## problem alot easier if I just created each node as an object and have object attributes like color and parent. Then I can create an object modifier( a class that modifies),
### each of the objects.

#I'll start from the objects themselves.

class Node:
    def __init__(self, name):
        self.name = name
        self.paths = []
        self.color = 'W'
        self.parent = None
#Then I guess ill create the object modifier and just name it DFS but have a few extra bells and whistles in it which let me do what I need to.
a, b, c, d, e= Node('A'), Node('B'), Node('C'), Node('D'), Node('E')
a.paths.extend([c,b])
b.paths.append(d)
d.paths.extend([a, e])
node_list = [a, b, c, d, e]
class DFS:
    def __init__(self, node_list):
        self.node_list = node_list
        self.search()
    def search(self):
        visual = ''
        arrow = '---->'
        for node in self.node_list:
            visual += node.name
            for path in node.paths:
                visual += arrow
                visual += path.name
            print(visual)
            visual = ''

```

```python



#An overview of data classes for working with gui modules
from dataclasses import dataclass
#Dataclasses defauklt perameters
# dataclass(cls=None, *, init=True, repr=True, eq=True, order=False, unsafehash=False, frozen=False)
#The default order value in the dataclasses module is set to False which means that by default we wont]
#be able to use all of the dunder comparison methods or function definitions such as lt, le, gt, ge.
#Setting the order parameter = to True allows us to take advantage of these class dunder methods.
#The frozen parameter set to True makes any proerty of an object immutable
#unsafehash set to true will give us a hash value for an object even if it is mutable

#Fields in dataclasses
#One of the abilities of using fields in dataclasses is for setting default values first by:
from dataclasses import field
class Person:
	name: str
	city: str
	age: int = field(default=25)

#Default factory: can only handle a function that requires no arguments or has no required parameters

def get_default_age():
	ages = [12,43, 56, 32, 22]
	return sum(ages) // len(ages)#Gives the avg of a range of ages

class Person:
	name: str
	city: str
	age: int = field(default_factory=get_default_age)


#Linked lists

class Node:
	def __init__(self, data=None):
		self.data = data
		self.next = None

class Chain:
	def __init__(self):
		self.head = Node()

	def append(self, data):
		new_node = Node(data)
		cur = self.head
		while cur.next != None:
			cur = cur.next
		cur.next = new_node
	def length(self):
		cur = self.head
		count = 0
		while cur.next != None:
			count += 1
			cur = cur.next
		return count
	def display(self):
		e = []
		e.clear()
		link = self.head
		while link.next != None:
			link = link.next
			e.append(link.data)
		return e
	def get(self, index):
		if index >= self.length():
			raise ValueError(f'{index} is out of range of the amount of {self.length()} items in the chain')
		cur_idx = 0
		cur_node = self.head
		while True:
			cur_node = cur_node.next
			if cur_idx == index: return cur_node.data
			cur_idx += 1
	def erase(self, index):
		if index >= self.length():
			raise ValueError(f'{index} is out of range of the amount of {self.length()} items in the chain')
		cur_idx = 0
		cur_node = self.head
		while True:
			last_node = cur_node
			cur_node = cur_node.next
			if cur_idx == index:
				last_node.next = cur_node.next
				return
			cur_idx += 1

class node:
	def __init__(self,data=None):
		self.data=data
		self.next=None

class Chain:
	def __init__(self):
		self.head=node()

	# Adds new node containing 'data' to the end of the linked list.
	def append(self,data):
		new_node=node(data)
		cur=self.head
		while cur.next!=None:
			cur=cur.next
		cur.next=new_node

	# Returns the length (integer) of the linked list.
	def length(self):
		cur=self.head
		total=0
		while cur.next!=None:
			total+=1
			cur=cur.next
		return total

	# Prints out the linked list in traditional Python list format. 
	def display(self):
		elems=[]
		cur_node=self.head
		while cur_node.next!=None:
			cur_node=cur_node.next
			elems.append(cur_node.data)
		print(elems)

	# Returns the value of the node at 'index'. 
	def get(self,index):
		if index>=self.length() or index<0: # added 'index<0' post-video
			print("ERROR: 'Get' Index out of range!")
			return None
		cur_idx=0
		cur_node=self.head
		while True:
			cur_node=cur_node.next
			if cur_idx==index: return cur_node.data
			cur_idx+=1

	# Deletes the node at index 'index'.
	def erase(self,index):
		if index>=self.length() or index<0: # added 'index<0' post-video
			print("ERROR: 'Erase' Index out of range!")
			return
		cur_idx=0
		cur_node=self.head
		while True:
			last_node=cur_node
			cur_node=cur_node.next
			if cur_idx==index:
				last_node.next=cur_node.next
				return
			cur_idx+=1

	# Allows for bracket operator syntax (i.e. a[0] to return first item).
	def __getitem__(self,index):
		return self.get(index)


	#######################################################
	# Functions added after video tutorial

	# Inserts a new node at index 'index' containing data 'data'.
	# Indices begin at 0. If the provided index is greater than or 
	# equal to the length of the linked list the 'data' will be appended.
	def insert(self,index,data):
		if index>=self.length() or index<0:
			return self.append(data)
		cur_node=self.head
		prior_node=self.head
		cur_idx=0
		while True:
			cur_node=cur_node.next
			if cur_idx==index:
				new_node=node(data)
				prior_node.next=new_node
				new_node.next=cur_node
				return
			prior_node=cur_node
			cur_idx+=1

	# Inserts the node 'node' at index 'index'. Indices begin at 0.
	# If the 'index' is greater than or equal to the length of the linked 
	# list the 'node' will be appended.
	def insert_node(self,index,node):
		if index<0:
			print("ERROR: 'Erase' Index cannot be negative!")
			return
		if index>=self.length(): # append the node
			cur_node=self.head
			while cur_node.next!=None:
				cur_node=cur_node.next
			cur_node.next=node
			return
		cur_node=self.head
		prior_node=self.head
		cur_idx=0
		while True:
			cur_node=cur_node.next
			if cur_idx==index:
				prior_node.next=node
				return
			prior_node=cur_node
			cur_idx+=1

	# Sets the data at index 'index' equal to 'data'.
	# Indices begin at 0. If the 'index' is greater than or equal 
	# to the length of the linked list a warning will be printed 
	# to the user.
	def set(self,index,data):
		if index>=self.length() or index<0:
			print("ERROR: 'Set' Index out of range!")
			return
		cur_node=self.head
		cur_idx=0
		while True:
			cur_node=cur_node.next
			if cur_idx==index:
				cur_node.data=data
				return
			cur_idx+=1


#Testing Class crap
class Node:
	def __init__(self, data=None):
		self.data = data
		self.next = None
class Chain(object):
	def __init__(self, head=None):
		self.head = head

	def append(self, new_element):
		current = self.head
		if self.head:
			while current.next:
				current = current.next
			current.next = new_element
		else:
			self.head = new_element
n = Node(f'DATA VALUE {5}')
n1 = Node(f'DATA VALUE {10}')
n2 = Node(f'DATA VALUE {20}')

def append(self, new_element):
        current = self.head
        if self.head:
            while current.next:
                current = current.next
            current.next = new_element
        else:
            self.head = new_element

"""The LinkedList code from before is provided below.
Add three functions to the LinkedList.
"get_position" returns the element at a certain position.
The "insert" function will add an element to a particular
spot in the list.
"delete" will delete the first element with that
particular value.
Then, use "Test Run" and "Submit" to run the test cases
at the bottom."""

class Element(object):
    def __init__(self, value):
        self.value = value
        self.next = None
class LinkedList(object):
    def __init__(self, head=None):
        self.head = head
    def append(self, new_element):
        current = self.head
        if self.head:
            while current.next:
                current = current.next
            current.next = new_element
        else:
            self.head = new_element
    def get_position(self, position):
        """Get an element from a particular position.
        Assume the first position is "1".
        Return "None" if position is not in the list."""
        return None
    def insert(self, new_element, position):
        """Insert a new node at the given position.
        Assume the first position is "1".
        Inserting at position 3 means between
        the 2nd and 3rd elements."""
        pass
    def delete(self, value):
        """Delete the first node with a given value."""
        pass

# Test cases
# Set up some Elements
e1 = Element(1)
e2 = Element(2)
e3 = Element(3)
e4 = Element(4)

# Start setting up a LinkedList
ll = LinkedList(e1)
ll.append(e2)
ll.append(e3)

# Test get_position
# Should print 3
print ll.head.next.next.value
# Should also print 3
print ll.get_position(3).value

# Test insert
ll.insert(e4,3)
# Should print 4 now
print ll.get_position(3).value

# Test delete
ll.delete(1)
# Should print 2 now
print ll.get_position(1).value
# Should print 4 now
print ll.get_position(2).value
# Should print 3 now
print ll.get_position(3).value


```

## Graphs


```python


#####GRAPHS
#Graph notes
''' Graph Rep
    Vertex object: Edges:___
    Edge Object: Vertices___
    Edge list: Just a list of edges (2D list)
    Adjacency list: A list of all the nodes which then stores the information about the nodes adjacent nodes. 
        If a node has only one adjacent node the node its adjacency list might look like this --> node_zero = [1]
        some more examples: node_one = [0, 2, 3], node_two = [1, 3], node_three = [1, 2]
    Adjacency Matrix: node_zero = [0, 1, 0, 0], node_one = [1, 0, 1, 1], node_two = [0, 1, 0, 1], node_three = [0, 1, 1, 0]
    so for the adjacency matrix we see each adjacent node in the matrix gets a value of 1. since there are 4 nodes total
    the matrix has 4 digits of either 1 or 0.
    Graph Traversal:
        DFS: Depth First Search: Where we follow one path as far as it will go
        BFS:Breadth First Search: Where we look at all the nodes adjacent to one before moving on to the next level
    Eulerian Paths:Travels through every edge in a path at least once.
    Eulerian cycle: You must traverse every edge only once and end up at the same node you started at. 
        not every graphg is a capable of having an eulerian path.
        graphs can only have eulerian cycles if all vertices have an even degree or an even number of edges connected to them
        eulerian paths are more leniant.
    Hamiltonian Path:??'''
class Graph:
	def __init__(self, edges):
		self.edges = edges
		self.graph_dict = {}
		for start, end in edges:
			if start in self.graph_dict:
				self.graph_dict[start].append(end)
			else:
				self.graph_dict[start] = [end]
		print(f'THE GRAPH: {self.graph_dict}')

	def get_paths(self, start, end, path=[]):
		path = path + [start]
		if start == end:
			return [path]
		if start not in self.graph_dict:
			return []
		paths = []
		for node in self.graph_dict[start]:
			if node not in path:
				new_paths = self.get_paths(node, end, path)
				for p in new_paths:
					paths.append(p)
		return paths


routes = [
        ("Mumbai", "Paris"),
        ("Mumbai", "Dubai"),
        ("Paris", "Dubai"),
        ("Paris", "New York"),
        ("Dubai", "New York"),
        ("New York", "Toronto"),
    ]


```

## Graph BFS

```python



class Vertex:
	def __init__(self, n):
		self.name = n
		self.neighbors = list()
		self.distance = 9999
		self.color = 'black'
	def add_neighbor(self, v):
		if v not in self.neighbors:
			self.neighbors.append(v)
			self.neighbors.sort()

class Graph:
	vertices = {}
	def add_vertex(self, vertex):
		if isinstance(vertex, Vertex) and vertex.name not in self.vertices:
			self.vertices[vertex.name] = vertex
			return True
		else:
			return False
	def add_edge(self, u, v):
		if u in self.vertices and v in self.vertices:
			for key, value in self.vertices.items():
				if key == u:
					value.add_neighbor(v)
				if key == v:
					value.add_neighbor(u)
			return True
		else:
			return False
	def print_graph(self):
		for key in sorted(list(self.vertices.keys())):
			print(key + str(self.vertices[key].neighbors) + "  " + str(self.vertices[key].distance))
	def bfs(self, vert):
		q = list()
		vert.distance = 0
		vert.color = 'red'
		for v in vert.neighbors:
			self.vertices[v].distance = vert.distance + 1
			q.append(v)
		while len(q) > 0:
			u = q.pop(0)
			node_u = self.vertices[u]
			node_u.color = 'red'
			for v in node_u.neighbors:
				node_v = self.vertices[v]
				if node_v.color == 'black':
					q.append(v)
					if node_v.distance > node_u.distance + 1:
						node_v.distance = node_u.distance + 1
g = Graph()
a = Vertex('A')
g.add_vertex(a)
g.add_vertex(Vertex('B'))
for i in range(ord('A'), ord('K')):
	g.add_vertex(Vertex(chr(i)))

edges = ['AB', 'AE', 'BF', 'CG', 'DE', 'DH', 'EH', 'FG', 'FI', 'FJ', 'GJ', 'HI']
for edge in edges:
	g.add_edge(edge[:1], edge[1:])
g.bfs(a)
g.print_graph()

class Vertex:
	def __init__(self, name):
		self.name = name
		self.neighbors = []
		self.distance = 9999
		self.color = None

	def add_neighbor(self, vertex):
		if vertex not in self.neighbors:
			self.neighbors.append(vertex)
			self.neighbors.sort()

class Graph:
	def __init__(self):
		self.vertices = {}

	def add_vertex(self, vertex):
		if isinstance(vertex, Vertex) and vertex.name not in self.vertices:
			self.vertices[vertex.name] = vertex
			return True
		return False

	def add_edge(self, side1, side2):
		if side1 in self.vertices and side2 in self.vertices:
			self.vertices[side1].add_neighbor(self.vertices[side2])
			self.vertices[side2].add_neighbor(self.vertices[side1])
			return True
		return False

	def pg(self):
		for key in sorted(list(self.vertices)):
			print(f'{key} {self.vertices[key].neighbors}  {self.vertices[key].distance}')

	def bfs(self, vert):
		q = []
		vert.distance = 0
		vert.color = 'RED'
		for v in vert.neighbors:
			self.vertices[v].distance = vert.distance + 1
			q.append(v)
		while q:
			u = q.pop(0)
			node_u = self.vertices[u]
			node_u.color = 'RED'
			for v in node_u.neighbors:
				node_v = self.vertices[v]
				if node_v.color == None:
					q.append(v)
					if node_v.distance > node_u.distance + 1:
						node_v.distance = node_u.distance + 1

def bfs_2(graph, node):
	visited = []
	q = []
	visited.append(node)
	q.append(node)
	while q:
		s = q.pop(0)
		print(s, end='')
		for n in graph[s]:
			if n not in visited:
				visited.append(n)
				q.append(n)

def bfs_3(graph, start_node):
	visited = []
	q = [start_node]
	while q:
		current_node = q.pop(0)
		visited.append(current_node)
		for neighbor in graph[current_node]:
			if neighbor not in visited:
				q.append(neighbor)
	return visited

def j_bfs(graph, start_node, visited=[]):
	visited.append(start_node)
	for node in graph[start_node]:
		if node not in visited:
			result = j_bfs(graph, node, visited)
			if result:
				visited.append(result)
	return visited
test_graph = {'0': ['3', '5', '9'], '1': ['6', '7', '4'],
'2': ['10', '5'], '3': ['0'], '4': ['1', '5', '8'],
'5': ['2', '0', '4'], '6': ['1'], '7': ['1'], '8': ['4'],
'9': ['0'], '10': ['2']}

def shortest_path(pre_node, start_node, end_node):
	path = [end_node]
	current_node = end_node
	while current_node != start_node:
		current_node = pre_node[current_node]
		path.append(current_node)
	path.reverse()
	return path

def bfs_shortest_path(graph, start_node, end_node):
	visited = []
	q = [start_node]
	pre_node = {}
	while q:
		current_node = q.pop(0)
		visited.append(current_node)
		for neighbor in graph[current_node]:
			if neighbor not in visited:
				q.append(neighbor)
				pre_node[neighbor] = current_node
	print(shortest_path(pre_node, start_node, end_node))
bfs_shortest_path(test_graph, '0', '1')

class Vertex:
	def __init__(self, name):
		self.name = name
		self.neighbors = []
		self.distance = None
		self.color = None

	def add_neighbor(self, vertex):
		if vertex not in self.neighbors:
			self.neighbors.append(vertex)

class Graph:
	def __init__(self):
		self.vertices = {}

	def add_vertex(self, vertex):
		if isinstance(vertex, Vertex) and vertex.name not in self.vertices:
			self.vertices[vertex.name] = vertex
			return True
		return False

	def add_edge(self, side1, side2):
		if side1 in self.vertices and side2 in self.vertices:
			self.vertices[side1].add_neighbor(self.vertices[side2])
			self.vertices[side2].add_neighbor(self.vertices[side1])
			return True
		return False

	def bfs(self, main_vert, log=[], q=[], root=None):
		root = root if root else main_vert.name
		main_vert.distance = main_vert.distance if main_vert.distance else 0
		if main_vert not in log:
			log.append(main_vert)
		for main_neighbor in main_vert.neighbors:
			if main_neighbor not in log:
				self.vertices[main_neighbor.name].distance = main_vert.distance + 1
				log.append(main_neighbor)
				q.append(main_neighbor)
		if q:
			return self.bfs(self.vertices[q.pop(0).name], log, q, root)
		output = {}
		for key in sorted(list(self.vertices)):
			output[key] = [(x.name, x.distance) for x in self.vertices[key].neighbors]
		return output

g = Graph()
a = Vertex('A')
g.add_vertex(a)
g.add_vertex(Vertex('B'))
for i in range(ord('A'), ord('L')):
	g.add_vertex(Vertex(chr(i)))

edges = ['AB', 'AE', 'BF', 'CG', 'CK', 'DE', 'DH', 'EH', 'FG', 'FI', 'FJ', 'GJ', 'HI']
for edge in edges:
	g.add_edge(edge[:1], edge[1:])
g.bfs(a)


```


## Graph DFS



```python


''' Types of DFS:
		|__Pre Order
		|__In order
		|__Post order'''
class Node:
    def __init__(self, name):
        self.name = name
        self.paths = []
        self.color = 'W'
        self.parent = None
#Then I guess ill create the object modifier and just name it DFS but have a few extra bells and whistles in it which let me do what I need to.
a, b, c, d, e= Node('A'), Node('B'), Node('C'), Node('D'), Node('E')
a.paths.extend([c,b])
b.paths.append(d)
d.paths.extend([a, e])
node_list = [a, b, c, d, e]
class DFS:
    def __init__(self, node_list):
        self.node_list = node_list
        self.search()
    def search(self):
    	keep = []
    	cycle = ''
    	visual = ''
    	arrow = '---->'
    	for node in self.node_list:
    		visual += node.name
    		for path in node.paths:
    			visual += arrow
    			visual += path.name
    			path.parent = node
    			if node.parent in keep and node.parent in path.paths:
    				cycle += path.name
    				cycle += arrow
    				cycle += node.parent.name
    				cycle += arrow
    				cycle += node.name
    				cycle += arrow
    				cycle += path.name + '--CYCLE REPEAT>--'
    				print(f'|CYCLE DETECTED| (CYCLE START> {cycle}')
    				cycle = ''
    		print(visual)
    		visual = ''
    		keep.append(node)
one = DFS(node_list)

```



## Linked Lists

```python


from dataclasses import dataclass, asdict, astuple
from typing import Optional

#In order for this linked list to work with dataclasses
#you need to remember to import the typing module, it allows you to have optional types
#as you object is instantiated
@dataclass
class Link:
	data: Optional[int] = None
	nxt: Optional[object] = None
@dataclass
class Chain:
	head: object = Link()
	def append(self, data):
		if data:
			now = self.head
			new_link = Link(data)
			while now.nxt:
				now = now.nxt
			now.nxt = new_link
		else:
			return 'YOU NEED TO GIMME SUH-IN TO WORK WIT PIMPIN! '
		return f'Your data {data} has been added to the list'
	def display(self):
		content = ()
		now = self.head
		while now.nxt:
			now = now.nxt
			content += now.data,
		return content
	def length(self):
		total = 0
		now = self.head
		while now.nxt:
			total += 1
			now = now.nxt
		return total
	def __len__(self):
		return self.length()
	def get(self, index):
		count = 0
		now = self.head
		if index >= 0 and index < self.length():
			while now.nxt:
				now = now.nxt
				if count == index:
					return now.data
				count += 1
			return now.data
		else:
			return f'index {index} is out of range breh!'
	def __getitem__(self,index):
		return self.get(index)
	def insert(self, index, data):
		count = 0
		now = self.head
		new_link = Link(data)
		if index >= 0 and index < self.length():
			while now.nxt:
				if not index:
					new_link.nxt = now.nxt
					now.nxt = new_link
					return f'The data {data} has been set to the index {index}'
				now = now.nxt
				if count == index - 1:
					new_link.nxt = now.nxt
					now.nxt = new_link
					return f'The data {data} has been set to the index {index}'
				count += 1
			else:
				return f'Your trying to insert data at the end of the list. Just use the append function for that!'
		else:
			return f'The index {index} is out of range'
	def set(self, index, data):
		count = 0
		now = self.head
		if index >= 0 and index < self.length():
			while now.nxt:
				now = now.nxt
				if count == index:
					now.data = data
					return f'The data at index {index} has been updated to {data}'
				count += 1
			else:
				now.data = data
		else:
			return f'The index {index} is out of range'
	def __setitem__(self, index, data):
		return self.set(index, data)
	def erase(self, index):
		count = 0
		now = self.head
		if index >= 0 and index < self.length():
			while now.nxt:
				if not index:
					popd = now.nxt.data
					now.nxt = now.nxt.nxt
					return popd
				now = now.nxt
				if count == index - 1:
					popd = now.nxt.data
					now.nxt = now.nxt.nxt
					return popd
				count += 1
		else:
			return f'Index {index} out of range! '
	def __delitem__(self, index):
		return self.erase(index)
	def pop(self, index=-1):
		now = self.head
		length = self.length()
		count = 0
		if length and index >= 0:
			return self.erase(index)
		if length:
			while now.nxt:
				if count == length - 1:
					output = now.nxt.data
					now.nxt = None
					return output
				now = now.nxt
				count += 1
		else:
			return 'There is nothing in the list'


#Without data class
#much lamer
class Node:
	def __init__(self, data=None):
		self.data = data
		self.next = None

class Chain:
	def __init__(self):
		self.head = Node()
	def append(self, data):
		now = self.head
		new = Node(data)
		while now.next:
			now = now.next
		now.next = new
	def __len__(self):
		now = self.head
		count = 0
		while now.next:
			now = now.next
			count += 1
		return count
	def display(self):
		elements = ()
		now = self.head
		while now.next:
			now = now.next
			elements += now.data,
		return elements
########
#Testing

######A TEST LINK LIST
@dataclass
class Node:
	''' A Node class that creates new nodes.....duh...:P'''
	data: Optional[int] = None
	_next: Optional[object] = None
@dataclass
class Linked:
	''' This class creates a new linked list'''
	head: object = Node()
	count: int = 0

	def append(self, data, head=None):
		node = head if head else self.head
		now = Node(data)
		if data:
			if node._next:
				return self.append(data, node._next)
			node._next = now
		return

	def show(self, head=None):
		node = head if head else self.head
		elements = ()
		if node._next:
			elements += node._next.data,
			elements += self.show(node._next)
		return elements

	def __len__(self):
		return len(self.show())

	def _mainlogic(self, index, data=None, head=None, switch=None):
		node = head if head else self.head
		if index >= 0 and index < self.__len__():
			if switch:
				new_node = Node(data)
				if not index:
					self.count = 0
					new_node._next = node._next
					node._next = new_node
					return
				elif index and self.count == index - 1:
					self.count = 0
					node = node._next
					new_node._next = node._next
					node._next = new_node
					return
			elif not switch and index == self.count:
				self.count = 0
				if data == 'get':
					return node._next.data
				elif data == 'del':
					node._next = node._next._next
					return
				elif data =='pop':
					popped = node._next.data
					node._next = node._next._next
					return popped
				node._next.data = data
				return
			self.count += 1
			return self._mainlogic(index, data, node._next, switch)

	def __setitem__(self, index, data):
		return self._mainlogic(index, data)

	def __getitem__(self, index):
		return self._mainlogic(index, 'get')

	def __delitem__(self, index):
		return self._mainlogic(index, 'del')
	def pop(self, index):
		return self._mainlogic(index, 'pop')

	def insert(self, index, data):
		return self._mainlogic(index, data, switch='insert')

```


## Binary Search Tree (BST)

```python


class BST:
	def __init__(self, data):
		self.data = data
		self.left = None
		self.right = None
	def add_child(self, data):
		if data == self.data:
			return f'{data} is already in the tree'
		if data < self.data:
			#ADD DATA TO LEFT SUBTREE
			if self.left:
				#CHECK IF THERE IS ALREADY A VALUE
				#IF THERE IS USE RECURSION
				#AND RUN IT THROUGH THIS METHOD AGAIN
				self.left.add_child(data)
			else:
				#IF THERE IS NO VALUE IN SELF.LEFT
				#THEN WE CAN CREATE THE OBJECT
				#SELF.LEFT AND SET ITS DATA VAL
				self.left = BST(data)
		if data > self.data:
			#ADD DATA TO RIGHT SUBTREE
			if self.right:
				#CHECK IF THERE IS ALREADY A SELF.
				#RIGHT
				self.right.add_child(data)
			else:
				self.right = BST(data)
	def iot(self):
		elements = []
		#CHECK THE LEFT SUBTREE
		if self.left:
			elements += self.left.iot()
		#CHECK BASE NODE
		elements.append(self.data)
		#CHECK THE RIGHT SUBTREE
		if self.right:
			elements += self.right.iot()
			return elements
	def prot(self):
		elements = [self.data]
		if self.left:
			elements += self.left.prot()
		if self.right:
			elements += self.right.prot()
		return elements
	def pot(self):
		elements = []
		if self.left:
			elements += self.left.pot()
		if self.right:
			elements += self.right.pot()
		elements.append(self.data)
		return elements
	def search(self, val):
		if self.data == val:
			return True
		if val < self.data:
			if self.left:
				return self.left.search(val)
			else:
				return False
		if val > self.data:
			if self.right:
				return self.right.search(val)
			else:
				return False


```

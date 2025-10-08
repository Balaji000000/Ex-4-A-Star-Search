ExpNo 4 : Implement A* search algorithm for a Graph
Name: Balaji N
Register Number:2305002002
Aim:
To ImplementA * Search algorithm for a Graph using Python 3.

Algorithm:
Initialize:

open_set = {start}, g[start] = 0, parents[start] = None.

While open_set not empty:

Pick node n with lowest f(n) = g[n] + H[n].

If n is goal → reconstruct and return path.

For each neighbor m of n:

Compute cost g[n] + weight.

If better, update g[m], parents[m], add m to open_set.

If loop ends without reaching goal → path doesn’t exist.

PROGRAM
graph, H = {}, {}
def AStar(start, goal):
    open_set, g, parents = [start], {start:0}, {start:None}
    while open_set:
        n = min(open_set, key=lambda x: g[x]+H[x])
        if n==goal:
            path=[]
            while n: path.append(n); n=parents[n]
            print("Path found:", path[::-1]); return
        open_set.remove(n)
        for m,w in graph.get(n,[]):
            cost=g[n]+w
            if m not in g or cost<g[m]:
                g[m]=cost; parents[m]=n
                if m not in open_set: open_set.append(m)
    print("Path does not exist!")
n,e=map(int,input().split())
for _ in range(e):
    u,v,w=input().split(); w=int(w)
    graph.setdefault(u,[]).append((v,w))
    graph.setdefault(v,[]).append((u,w))
for _ in range(n):
    node,h=input().split(); H[node]=int(h)
AStar(input(),input())
GRAPH
WhatsApp Image 2025-10-06 at 13 57 02_c28f6507

INPUT
3 2
A B 1
B C 2
A 3
B 1
C 0
A
C
Output
image
RESULT:
Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.

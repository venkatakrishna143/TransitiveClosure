# A class to represent a graph object
class Graph:
    def __init__(self, edges, N):
 
        self.adjList = [[] for _ in range(N)]
 
        for (src, dest) in edges:
            self.adjList[src].append(dest)
 
 
def DFS(graph, C, root, descendant):
 
    for child in graph.adjList[descendant]:
        if C[root][child] == 0:
            C[root][child] = 1
            DFS(graph, C, root, child)
 
 
if __name__ == '__main__':
 
    edges = [(0, 2), (1, 0), (3, 1)]
 
    N = 4
 
    graph = Graph(edges, N)
 
    C = [[0 for x in range(N)] for y in range(N)]
 
    for v in range(N):
        C[v][v] = 1
        DFS(graph, C, v, v)
 
        print(C[v])

# DS_Module17
# EX.NO : 5(A) Representation of Graph
## DATE:
## AIM:
To write a C program to display the adjacency matrix of the given graph by supplying the edges and the number of vertices.

## Algorithm
1.Start<br/>
2.Read the value of V (number of vertices).<br/>
3.Declare an adjacency matrix adjMatrix[V][V].<br/>
4.Initialize the matrix to 0 using the init function.<br/>
5.Calculate the maximum number of edges me as n * (n - 1) / 2.<br/>
6.For each edge, read e1 and e2, add the edge to the adjacency matrix, and stop if e1 == -1 && e2 == -1.<br/>
7.Print the adjacency matrix.<br/>
8.End<br/>

## Program:
```
Program to display the adjacency matrix of the given graph
Developed by:LOKESH RAHUL V V
RegisterNumber: 212222100024
```
```
 
/*#include<stdio.h> 
int V; 
 
//init matrix to 0 
void init(int arr[][V]) 
{ 
int i,j; 
for(i = 0; i < V; i++) 
for(j = 0; j < V; j++) 
arr[i][j] = 0; 
} 
*/ 
int main() 
{ int e1,e2,me,n,i; 
scanf("%d",&V); 
int adjMatrix[V][V]; 
init(adjMatrix); 
n=V; 
me=n*(n-1)/2; 
for(i=0;i<me;i++) 
{ 
scanf("%d%d",&e1,&e2); 
addEdge(adjMatrix,e1,e2); 
if(e1==-1 && e2==-1) 
{ 
break; 
} 
} 
printAdjMatrix(adjMatrix); 
 
}

```
## Output:
![image](https://github.com/user-attachments/assets/9cafac08-59cc-412e-8e7d-b5b77ff8023a)



## Result:
Thus, the C program to print the adjacency matrix of the given graph is implemented successfully.
# Ex22 Breadth First Graph
## DATE:
## AIM:
To write a printQueue C function of the given graph that is to be traversed in the breadth first manner.

![image](https://github.com/user-attachments/assets/f483f48c-6af0-4027-a993-01c108a50933)


## Algorithm
1.Check if the queue is empty using isEmpty(q). If true, print "Queue is empty".

2.If not empty, print "Queue contains ".

3.Initialize a loop variable i to q->front.

4.Use a for loop to iterate from q->front to q->rear, printing each item in q->items[i].

5.End the loop and function after printing all items.

## Program:
```
/*
Program to traverse graph using BFS
Developed by:LOKESH RAHUL V V
RegisterNumber: 212222100024
*/
void printQueue(struct queue* q) {
  int i = q->front;
 
  if (isEmpty(q)) {
    printf("Queue is empty");
  } else { 
    printf("Queue contains ");
    for (i = q->front; i < q->rear + 1; i++) {
      printf("%d ", q->items[i]);
    }
   }
}
```

## Output:
![image](https://github.com/user-attachments/assets/ad264a47-4a8b-4a3d-95a6-0e52829cfa72)



## Result:
Thus, the code for the printQueue function of the following graph that is to be traversed in the breadth first manner is implemented successfully.
# Ex23 Depth First Graph
## DATE:
## AIM:
To compose the code for the function createNode to traverse the graph below in the depth first fashion.

![image](https://github.com/user-attachments/assets/63552824-d0a3-49c6-a473-6db27d1f03e4)

## Algorithm


1. **Allocate Memory**: Use `malloc` to allocate memory for a new node of type `struct node`.<br/>
2. **Initialize Vertex**: Set the `vertex` field of the new node to the value `v`.<br/>
3. **Initialize Next Pointer**: Set the `next` pointer of the new node to `NULL`.<br/>
4. **Return Node**: Return the pointer to the newly created node.<br/>
5. **End Function**: Complete the function execution.  <br/>

## Program:
```
/*
Program to traverse the graph below in the depth first fashion
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
*/
struct node* createNode(int v) {
  struct node* newNode = malloc(sizeof(struct node));
  newNode->vertex = v;
  newNode->next = NULL;
  return newNode;
}

```

## Output:

![image](https://github.com/user-attachments/assets/69faff9c-d616-47c5-921c-a614214bb43f)


## Result:
Thus, the C code for the function createNode to traverse the graph below in the depth first fashion is implemented successfully
# Ex24 Topological Sort
## DATE:
## AIM:
To compose the code to determine whether the topological ordering for the following graph is possible or not.

![image](https://github.com/user-attachments/assets/c74a7111-9b59-475c-aad4-9baf23d50ec0)


## Algorithm
1. Initialize variables: 
   - Declare `i`, `v`, `count`, `topo_order[MAX]`, and `indeg[MAX]`.<br>
   
2. Create the graph: 
   - Call `create_graph()` to initialize the graph structure.<br>
   
3. Calculate indegree for each vertex: 
   - For each vertex `i` from `0` to `n-1`:<br>
     - Calculate `indeg[i]` using `indegree(i)`.<br>
     - If `indeg[i]` is `0`, insert vertex `i` into the queue using `insert_queue(i)`.<br>
   
4. Perform topological sorting: 
   - Initialize `count` to `0`.<br>
   - While the queue is not empty and `count` is less than `n`:<br>
     - Remove vertex `v` from the queue using `delete_queue()`.<br>
     - Add vertex `v` to `topo_order` at index `++count`.<br>
     - For each vertex `i` from `0` to `n-1`:<br>
       - If there is an edge from `v` to `i` (i.e., `adj[v][i] == 1`):<br>
         - Remove the edge by setting `adj[v][i]` to `0`.<br>
         - Decrease `indeg[i]` by `1`.<br>
         - If `indeg[i]` becomes `0`, insert vertex `i` into the queue.<br>
   
5. Check for cycles: 
   - If `count` is less than `n`, print "No topological ordering possible, graph contains cycle" and exit the program.<br>
   
6. Print the topological order: 
   - Print "Vertices in topological order are:".<br>
   - For each index `i` from `1` to `count`, print `topo_order[i]`.<br>
   
7. End the program: 
   - Return `0` to indicate successful completion.<br>
## Program:
```
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
*/
int main()
{
        int i,v,count,topo_order[MAX],indeg[MAX];

        create_graph();

        /*Find the indegree of each vertex*/
        for(i=0;i<n;i++)
        {
                indeg[i] = indegree(i);
                if( indeg[i] == 0 )
                        insert_queue(i);
        }

        count = 0;

        while(  !isEmpty_queue( ) && count < n )
        {
                v = delete_queue();
        topo_order[++count] = v; /*Add vertex v to topo_order array*/
                /*Delete all edges going from vertex v */
                for(i=0; i<n; i++)
                {
                        if(adj[v][i] == 1)
                        {
                                adj[v][i] = 0;
                                indeg[i] = indeg[i]-1;
                                if(indeg[i] == 0)
                                        insert_queue(i);
                        }
                }
        }

        if( count < n )
        {
                printf("No topological ordering possible, graph contains cycle\n");
                exit(1);
        }
        printf("Vertices in topological order are :\n");
        for(i=1; i<=count; i++)
                printf( "%d ",topo_order[i] );
        printf("\n");

        return 0;
}/*End of main()*/
```

## Output:


![image](https://github.com/user-attachments/assets/8845165c-ad03-49d2-a955-1552731101e1)

## Result:
Thus, the C program for determining whether the topological ordering for the following graph is possible or not, is implemented successfully.
# Ex25 Adjacency List Representation
## DATE:
## AIM:
To write a C program to represent the given graph using the adjacency list.

## Algorithm
1. Initialize variables: 
   - Declare `n` and `i` as integers.<br>
   
2. Read the number of vertices: 
   - Use `scanf` to read the value of `N` (number of vertices).<br>
   - Use `scanf` to read the value of `n` (number of edges).<br>
   
3. Input edges of the graph: 
   - Declare an array `edges` of type `struct Edge` with size `n`.<br>
   - For each edge `i` from `0` to `n-1`:<br>
     - Use `scanf` to read the source vertex `edges[i].src`.<br>
     - Use `scanf` to read the destination vertex `edges[i].dest`.<br>
   
4. Construct the graph: 
   - Call `createGraph(edges, n)` to create a graph from the given edges and store the result in `graph`.<br>
   
5. Print the graph: 
   - Call `printGraph(graph)` to print the adjacency list representation of the graph.<br>
   
6. End the program: 
   - Return `0` to indicate successful completion.<br>

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
*/
int main(void)
{   int n,i;
    scanf("%d",&N);
    scanf("%d",&n);
    // input array containing edges of the graph (as per the above diagram)
    // (x, y) pair in the array represents an edge from x to y
    struct Edge edges[n];
    for (i = 0; i < n; i++)
    {
        // get the source and destination vertex
        scanf("%d",&edges[i].src);
        scanf("%d",&edges[i].dest);
      
    }
   
    // construct a graph from the given edges
    struct Graph *graph = createGraph(edges, n);
 
    // Function to print adjacency list representation of a graph
    printGraph(graph);
 
    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/f2037eca-349c-4f3d-b48e-e2b1a1c942d7)


## Result:
Thus, the C program to represent the given graph using the adjacency list is implemented successfully

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
Developed by: ASHWIN KUMAR S
RegisterNumber: 212222240013
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

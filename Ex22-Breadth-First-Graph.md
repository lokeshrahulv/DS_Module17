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
Developed by: ASHWIN KUMAR S
RegisterNumber: 212222240013
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

# Ex28 Dijkstra’s Algorithm
## DATE:25/4/25
## AIM:
To write a C Program to implement Dijkstra's Algorithm to find the shortest path

## Algorithm
1. Initialize constants and global variables: 
   - Define `INFINITY` as `9999` and `MAX` as `10`.<br>

2. Define the function `dijkstra(int G[MAX][MAX], int n, int startnode)` to compute the shortest paths from the starting node.<br>

3. In the `main` function:<br>
   - Declare a 2D array `G[MAX][MAX]`, and integers `i`, `j`, `n`, and `u`.<br>
   - Read the number of nodes `n` using `scanf`.<br>
   - For each node `i` from `0` to `n-1`:<br>
     - For each node `j` from `0` to `n-1`:<br>
       - Read the edge weights into the adjacency matrix `G[i][j]` using `scanf`.<br>
   - Read the starting node `u` using `scanf`.<br>
   - Call the `dijkstra(G, n, u)` function to compute the shortest paths.<br>
   - Return `0` to indicate successful completion.<br>

4. In the `dijkstra(int G[MAX][MAX], int n, int startnode)` function:<br>
   - Declare local variables `cost[MAX][MAX]`, `distance[MAX]`, `pred[MAX]`, `visited[MAX]`, `count`, `mindistance`, `nextnode`, `i`, and `j`.<br>
   - Create the cost matrix:<br>
     - For each node `i` from `0` to `n-1`:<br>
       - For each node `j` from `0` to `n-1`:<br>
         - If `G[i][j]` is `0`, set `cost[i][j]` to `INFINITY`; otherwise, set `cost[i][j]` to `G[i][j]`.<br>
   - Initialize the `pred[]`, `distance[]`, and `visited[]` arrays:<br>
     - For each node `i` from `0` to `n-1`:<br>
       - Set `distance[i]` to `cost[startnode][i]` and `pred[i]` to `startnode`, and set `visited[i]` to `0`.<br>
     - Set `distance[startnode]` to `0` and `visited[startnode]` to `1`.<br>
   - Initialize `count` to `1`.<br>
   - While `count` is less than `n-1`:<br>
     - Set `mindistance` to `INFINITY`.<br>
     - For each node `i` from `0` to `n-1`:<br>
       - If `distance[i]` is less than `mindistance` and `visited[i]` is `0`, update `mindistance` and `nextnode` with the current node.<br>
     - Mark `nextnode` as visited.<br>
     - For each node `i` from `0` to `n-1`:<br>
       - If `visited[i]` is `0` and if a better path exists through `nextnode`, update `distance[i]` and `pred[i]`.<br>
     - Increment `count` by `1`.<br>

5. Print the shortest path and distance for each node:<br>
   - For each node `i` from `0` to `n-1`:<br>
     - If `i` is not equal to `startnode`, print the distance from the starting node to `i`.<br>
     - Print the path from `i` back to `startnode` using the `pred[]` array.<br>
     - Use a loop to trace back the path from `i` to `startnode` and print each node in the path.<br>

## Program:
```
/*
Program to implement Dijkstra's Algorithm 
Developed by: PREM R
RegisterNumber:  212223240124
*/
#include<stdio.h>
#define INFINITY 9999
#define MAX 10
 
void dijkstra(int G[MAX][MAX],int n,int startnode);
 
int main()
{
int G[MAX][MAX],i,j,n,u;
scanf("%d",&n);
for(i=0;i<n;i++)
for(j=0;j<n;j++)
scanf("%d",&G[i][j]);
scanf("%d",&u);
dijkstra(G,n,u);
return 0;
}
 
void dijkstra(int G[MAX][MAX],int n,int startnode)
{
 
int cost[MAX][MAX],distance[MAX],pred[MAX];
int visited[MAX],count,mindistance,nextnode,i,j;
//pred[] stores the predecessor of each node
//count gives the number of nodes seen so far
//create the cost matrix
for(i=0;i<n;i++)
for(j=0;j<n;j++)
if(G[i][j]==0)
cost[i][j]=INFINITY;
else
cost[i][j]=G[i][j];
//initialize pred[],distance[] and visited[]
for(i=0;i<n;i++)
{
distance[i]=cost[startnode][i];
pred[i]=startnode;
visited[i]=0;
}
distance[startnode]=0;
visited[startnode]=1;
count=1;
while(count<n-1)
{
mindistance=INFINITY;
//nextnode gives the node at minimum distance
for(i=0;i<n;i++)
if(distance[i]<mindistance&&!visited[i])
{
mindistance=distance[i];
nextnode=i;
}
//check if a better path exists through nextnode
visited[nextnode]=1;
for(i=0;i<n;i++)
if(!visited[i])
if(mindistance+cost[nextnode][i]<distance[i])
{
distance[i]=mindistance+cost[nextnode][i];
pred[i]=nextnode;
}
count++;
}
 
//print the path and distance of each node
for(i=0;i<n;i++)
if(i!=startnode)
{
printf("Distance of node%d=%d\n",i,distance[i]);
printf("Path=%d",i);
j=i;
do
{
j=pred[j];
printf("<-%d",j);
}while(j!=startnode);
}
}

```

## Output:

***![image](https://github.com/user-attachments/assets/121d86c2-a203-4174-aa9d-5389b62714ef)



## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.

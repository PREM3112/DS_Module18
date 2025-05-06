# Ex30 Finding Total Cost of Spanning Tree
## DATE:25/4/2025
## AIM:
To write a C Program to implement Prim's Algorithm for finding Total Cost of spanning tree.
## Algorithm
1. Initialize constants and global variables: 
   - Define `infinity` as `9999` and `MAX` as `20`. 
   - Declare matrices `G[MAX][MAX]`, `spanning[MAX][MAX]`, and an integer `n`.<br>

2. Define the function `prims()` to compute the minimum spanning tree.<br>

3. In the `main` function:<br>
   - Declare variables `i`, `j`, and `total_cost` as integers.<br>
   - Read the number of vertices `n` using `scanf`.<br>
   - For each vertex `i` from `0` to `n-1`:<br>
     - For each vertex `j` from `0` to `n-1`:<br>
       - Read the edge weights into the adjacency matrix `G[i][j]` using `scanf`.<br>
   - Call the `prims()` function and store the result in `total_cost`.<br>
   - For each vertex `i` from `0` to `n-1`:<br>
     - For each vertex `j` from `0` to `n-1`:<br>
       - Print the spanning tree matrix `spanning[i][j]`.<br>
     - Print a newline.<br>
   - Print the total cost of the spanning tree.<br>
   - Return `0` to indicate successful completion.<br>

4. In the `prims()` function:<br>
   - Declare local variables `cost[MAX][MAX]`, `u`, `v`, `min_distance`, `distance[MAX]`, `from[MAX]`, `visited[MAX]`, `no_of_edges`, `i`, `min_cost`, and `j`.<br>
   - Create the `cost[][]` matrix and initialize the `spanning[][]` matrix:<br>
     - For each vertex `i` from `0` to `n-1`:<br>
       - For each vertex `j` from `0` to `n-1`:<br>
         - If `G[i][j]` is `0`, set `cost[i][j]` to `infinity`; otherwise, set `cost[i][j]` to `G[i][j]` and initialize `spanning[i][j]` to `0`.<br>
   - Initialize the `visited[]`, `distance[]`, and `from[]` arrays:<br>
     - Set `distance[0]` to `0` and `visited[0]` to `1`.<br>
     - For each vertex `i` from `1` to `n-1`:<br>
       - Set `distance[i]` to `cost[0][i]` and `from[i]` to `0`, and set `visited[i]` to `0`.<br>
   - Initialize `min_cost` to `0` and `no_of_edges` to `n-1`.<br>
   - While `no_of_edges` is greater than `0`:<br>
     - Set `min_distance` to `infinity`.<br>
     - For each vertex `i` from `1` to `n-1`:<br>
       - If `visited[i]` is `0` and `distance[i]` is less than `min_distance`, update `v` and `min_distance` with the current vertex.<br>
     - Set `u` to `from[v]`.<br>
     - Insert the edge in the spanning tree by updating `spanning[u][v]` and `spanning[v][u]` with `distance[v]`.<br>
     - Decrement `no_of_edges` and set `visited[v]` to `1`.<br>
     - Update the `distance[]` array:<br>
       - For each vertex `i` from `1` to `n-1`:<br>
         - If `visited[i]` is `0` and `cost[i][v]` is less than `distance[i]`, update `distance[i]` and `from[i]`.<br>
     - Add `cost[u][v]` to `min_cost`.<br>
   - Return `min_cost` as the total cost of the minimum spanning tree.<br>

## Program:
```
/*
Program to implement Prim's Algorithm for finding Total Cost of spanning tree.
Developed by: PREM R
RegisterNumber:  212223240124
*/
#include<stdio.h>
#include<stdlib.h>
 
#define infinity 9999
#define MAX 20
 
int G[MAX][MAX],spanning[MAX][MAX],n;
 
int prims();
 
int main()
{
int i,j,total_cost;
scanf("%d",&n);
for(i=0;i<n;i++)
for(j=0;j<n;j++)
scanf("%d",&G[i][j]);
total_cost=prims();

for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
printf("%d ",spanning[i][j]);
printf("\n");
}
printf("\nTotal cost of spanning tree=%d",total_cost);
return 0;
}
 
int prims()
{
int cost[MAX][MAX];
int u,v,min_distance,distance[MAX],from[MAX];
int visited[MAX],no_of_edges,i,min_cost,j;
//create cost[][] matrix,spanning[][]
for(i=0;i<n;i++)
for(j=0;j<n;j++)
{
if(G[i][j]==0)
cost[i][j]=infinity;
else
cost[i][j]=G[i][j];
spanning[i][j]=0;
}
//initialise visited[],distance[] and from[]
distance[0]=0;
visited[0]=1;
for(i=1;i<n;i++)
{
distance[i]=cost[0][i];
from[i]=0;
visited[i]=0;
}
min_cost=0; //cost of spanning tree
no_of_edges=n-1; //no. of edges to be added
while(no_of_edges>0)
{
//find the vertex at minimum distance from the tree
min_distance=infinity;
for(i=1;i<n;i++)
if(visited[i]==0&&distance[i]<min_distance)
{
v=i;
min_distance=distance[i];
}
u=from[v];
//insert the edge in spanning tree
spanning[u][v]=distance[v];
spanning[v][u]=distance[v];
no_of_edges--;
visited[v]=1;
//updated the distance[] array
for(i=1;i<n;i++)
if(visited[i]==0&&cost[i][v]<distance[i])
{
distance[i]=cost[i][v];
from[i]=v;
}
min_cost=min_cost+cost[u][v];
}
return(min_cost);
}
```

## Output:

![image](https://github.com/user-attachments/assets/551b82e4-0ef7-413c-91cc-c3d55c6e454d)



## Result:
Thus the C program to implement Prim's Algorithm for finding Total Cost of spanning tree is implemented successfully.

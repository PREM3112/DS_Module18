# Ex27 Kruskal’s Algorithm
## DATE:25/4/25
## AIM:
To write a C program to implement Kruskal's Algorithm for finding minimum cost

## Algorithm
1. Initialize global variables: 
   - Declare integers `i`, `j`, `k`, `a`, `b`, `u`, `v`, `n`, `ne` (set to `1`), `min`, `mincost` (set to `0`), and a 2D array `cost[9][9]`, and an array `parent[9]`.<br>

2. Define the function `find(int)` to find the root of a vertex.<br>

3. Define the function `uni(int, int)` to perform union of two sets.<br>

4. In the `main` function:<br>
   - Read the number of vertices `n` using `scanf`.<br>
   - For each vertex `i` from `1` to `n`:<br>
     - For each vertex `j` from `1` to `n`:<br>
       - Read the edge weights into the `cost[i][j]` matrix using `scanf`.<br>
       - If `cost[i][j]` is `0`, set it to `999` (representing infinity).<br>
   
5. While the number of edges `ne` is less than `n`:<br>
   - For each vertex `i` from `1`, initialize `min` to `999`:<br>
     - For each vertex `j` from `1` to `n`:<br>
       - If `cost[i][j]` is less than `min`, update `min`, `a`, `u`, `b`, and `v` with the current edge values.<br>
   
6. Find the roots of vertices `u` and `v` using the `find(u)` and `find(v)` functions.<br>

7. If `uni(u, v)` returns `1` (indicating they belong to different sets):<br>
   - Print the edge and its cost: `printf("%d edge (%d,%d) =%d\n", ne++, a, b, min);`.<br>
   - Add `min` to `mincost`.<br>
   
8. Set `cost[a][b]` and `cost[b][a]` to `999` to exclude this edge from future consideration.<br>

9. Print the total minimum cost of the spanning tree: `printf("Minimum cost = %d\n", mincost);`.<br>

10. Return `0` to indicate successful completion.<br>

11. In the `find(int i)` function:<br>
   - While `parent[i]` is not `0`, update `i` to `parent[i]`.<br>
   - Return the root of the set.<br>

12. In the `uni(int i, int j)` function:<br>
   - If `i` is not equal to `j`, set `parent[j]` to `i` and return `1` (indicating a successful union).<br>
   - Return `0` if they are already in the same set.<br>

## Program:
```
/*
Program to implement Kruskal's Algorithm
Developed by: PREM R
RegisterNumber:  212223240124
*/
    #include <stdio.h>
    #include <stdlib.h>
    int i,j,k,a,b,u,v,n,ne=1;
    int min,mincost=0,cost[9][9],parent[9];
    int find(int);
    int uni(int,int);
    int main()
    {
          scanf("%d",&n);
          for(i=1;i<=n;i++)
     {
     for(j=1;j<=n;j++)
     {
     scanf("%d",&cost[i][j]);
     if(cost[i][j]==0)
     cost[i][j]=999;
     }
     }
         while(ne < n)
     {
     for(i=1,min=999;i<=n;i++)
     {
     for(j=1;j <= n;j++)
     {
     if(cost[i][j] < min)
     {
     min=cost[i][j];
     a=u=i;
     b=v=j;
     }
     }
     }
     u=find(u);
     v=find(v);
     if(uni(u,v))
     {
     printf("%d edge (%d,%d) =%d\n",ne++,a,b,min);
     mincost +=min;
     }
     cost[a][b]=cost[b][a]=999;
     }
     printf("Minimum cost = %d\n",mincost);
     return 0;
       }
    int find(int i)
    {
     while(parent[i])
     i=parent[i];
     return i;
    }
    int uni(int i,int j)
    {
     if(i!=j)
     {
     parent[j]=i;
     return 1;
     }
     return 0;
    }

```

## Output:

![image](https://github.com/user-attachments/assets/12b2ed8b-bc94-495d-b5d3-22eabb5c0e1f)



## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.

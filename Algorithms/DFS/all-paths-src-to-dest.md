## Given a graph you want to find all the paths from Src to Given Dest

**In this problem we just want to find all possible paths from given src to destination so we use dfs calls**
**We keep track of visited array and only unvisit the destination at each path ending for calling out new path**

```
#include<bits/stdc++.h>

using namespace std;

class Graph{
  int V;
  list<int>* adj;//adjacency list

  void printAllPathsUtil(int,int,bool[],int[],int&);
public:
  Graph(int V);
  void addEdge(int u,int v);
  void printAllPaths(int src,int des);

};

Graph::Graph(int V)
{
  this->V=V;
  adj=new list<int>[V];
}
void Graph::addEdge(int u,int v)
{
  adj[u].push_back(v);
}
void Graph::printAllPaths(int s,int d)
{
  bool* vis=new bool[V];
  int* path=new int[V];
  int path_index=0;
  for(int i=0;i<V;i++)
  {
    vis[i]]=false;
  }
  printAllPathsUtil(s,d,vis,path,path_index);
}
printAllPathsUtil(int u,int d,bool vis[],int path[],int& path_index){
  vis[u]=true;
  path[path_index]=u;
  path_index++;

  if(u==d)
  {
    for(int i=0;i<path_index;i++)
    {
      cout<<path[i]<<" ";
    }
    cout<<"\n";
  }else{
    list<int>::iterator it;
    for(it=adj[u].begin();it!=adj[u].end();++it)
    {
      if(!vis[*it])
      {
        printAllPathsUtil(*it,d,vis,path,path_index);
      }
    }
    path_index--;
    vis[u]=false;
  }
}

```

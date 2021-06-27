
# DFS

### DFS Traversals using Matrix and Adj List

#### C++ and C 

**We Call DFSUtil from DFS and in DFS we check for connected Components**

```
#include<bits/stdc++.h>

using namespace std;

class Graph{
  void DFSUtil(int v);
public:
  map<int,bool> vis;
  map<int,list<int>> adj;
  void addEdge(int v,int w);

  void DFS();
}

void Graph::addEdge(int v,int w)
{
  adj[v].push_back(w);
}
void Graph::DFSUtil(int v)
{
  vis[v]=true;
  cout<<v<<" ";
  list<int>::iterator it;
  for(it=adj[v].begin();it!=adj[v].end();++it)
  {
    if(!vis[*it])
    {
      DFSUtil(*it);
    }
  }
}


void Graph::DFS()
{
  for(auto i:adj)
  {
    if(vis[i.first]==false)
    {
      DFSUtil(i.first);
    }
  }
}


```

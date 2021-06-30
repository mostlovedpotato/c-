## Question from Atcoder contest 204 problem C Tour

### Main Concept needed is Dfs

**[Problem Statement](https://atcoder.jp/contests/abc204/tasks/abc204_c)**

**Problem basically asks the number of vertices reachable from each vertex total count**
**We count all reachable vertices from given vertex and do the same for each vertex in graph**
**Time complexity for each iteration for one vertext would be O(M+N) and traversing all vertex would lead to O(N(M+N))**

```
#include<bits/stdc++.h>

using namespace std;

vector<int>mp[2000];
int vis[2000];

// vector<vector<int>> graph;
// void dfs(int v)
// {
//   if(temp[v]) return;
//   temp[v]=true;
//   for(auto u:graph[v])dfs(u);
// }

void dfs(int s)
{
  vis[s]=1;
  for(int u:mp[s])
  {
    if(!vis[u]){
      dfs(u);
    }
  }
}

void solve()
{
  int n,m;
  cin>>n>>m;
  graph.resize(n);
  for(int i=0;i<m;i++)
  {
    int a,b;
    cin>>a>>b;
    graph[a-1].push_back(b-1);
  }
  int ans=0;
  for(int i=0;i<n;i++)
  {
    for(int j=0;j<n;j++)
    {vis[j]=false;}
    dfs(i);
    for(int j=0;j<n;j++)
    {
      if(vis[j])
      {
        ans++;
      }
    }
  }
  cout<<ans<<endl;
}

int main()
{
  solve();
  return 0;
}

```

## This Problem is from Geeks For Geeks 
### In this problem we want to find the paths from starting vertex given 0,0 to dest n-1,n-1 

**[Problem Link](https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)**

**To approach this problem we will do dfs call in every direction by passing string and updating it on each call**

```
class Solution{
    public:
    vector<string> ans;
    
    void dfs(vector<vector<int>> &m, int i,int j,int n,string str){
        if( i>=n || j>=n || i<0 || j<0 || m[i][j] == 0)return;
        if( i==n-1 && j==n-1){
            ans.push_back(str);
            return;
        }
        
        m[i][j]=0;
        dfs(m,i+1,j,n,str+"D");
        dfs(m,i,j+1,n,str+"R");
        dfs(m,i,j-1,n,str+"L");
        dfs(m,i-1,j,n,str+"U");
        m[i][j]=1;
    }
    
    vector<string> findPath(vector<vector<int>> &m, int n) {
        // Your code goes here
        ans.clear();
         if (m[0][0] == 0 || m[n - 1][n - 1] == 0) return ans;
        dfs(m,0,0,n,"");
         sort(ans.begin(), ans.end());
       // if(ans.size() ==0 )ans.push_back("-1");
        return ans;

    }};
```

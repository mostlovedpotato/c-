### Problem Link : 
**[Problem A](https://vjudge.net/contest/474216#problem/A)**

Below is the code : 

```
const int INF = 1e6;
vector<int> spg(INF,0);

void sol(){
	spg[1]=0;
	for(int i=1;i<INF;i++){
		int x = i,y=i;
		while(x!=0){
			x=x%10;
			y+=x;
			x/=10;
		}
		if(spg[y]==0)
			spg[y]=i;
		else{
			spg[y]=min(i,spg[y]);
		}
	}
}

void solve() {
    int n;re(n);
    cout << spg[n] << endl;
}
```

#### Call sol() once before the test cases.

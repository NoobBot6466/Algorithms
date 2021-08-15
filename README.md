# The Tortoise and the Hare (Floyd’s Algorithm)
https://medium.com/@tuvo1106/the-tortoise-and-the-hare-floyds-algorithm-87badf5f7d41
# vetor input
http://www.cplusplus.com/forum/beginner/145093/



**Topological sort and detection of cycle in DAC( directed cyclic graph) using kahn's algorithm**


#include<bits/stdc++.h>
using namespace std;
const int n=100000;
vector<int> adj[n];
vector<int> indegree(n,0);
vector<int> toposort;
void kahn(int node)
{
	
	queue<int > q;
	for(int i=0;i<node;i++)
	{
		for(auto x : adj[i])
			indegree[x]++; ///indegree[x] =indegree[x] + 1;
	}
//	cout << " indegree of node 0 to N respectively"<<endl;
//	for(auto x: indegree)
//		cout<< x <<" ";
//		cout<<endl;
	for(int i=0;i<node;i++)
	{
		if(indegree[i]==0)
			q.push(i);
	}
	int count=0;
	while(!q.empty())
	{
		int f=q.front();
		q.pop();
		count++;
		toposort.push_back(f);
		for(auto x: adj[f])
		{
			indegree[x]--;  // indgree[x]= indgree[x] + 1;
			if(indegree[x]==0)
				q.push(x);	
		}
	}
	if(count==node)
	{
		cout<< "Toposort for the graph will be "<<endl;
		for(auto x: toposort)
		cout<< x<<" ";	
	}
	else
		cout <<"There is a cycle in the graph"<<endl;
	
}
main()
{
	int node,edge;
	cin>>node>>edge;
	for(int i=0;i<edge;i++)
	{
		int u,v; cin >>u>>v;
		adj[u].push_back(v); //dag
	}
	
	kahn(node);
}
	
	
**sieve of eratosthenes**
	
#include<bits/stdc++.h>
using namespace std;
main()
{
  int n;
  cin>>n;
  bool arr[n+1];
  memset(arr,true,sizeof(arr));
  
  for(int i=2;i<=sqrt(n);i++)
  {
  	if(arr[i]==true)
  	{
  		for(int j=i*i;j<=n;j=j+i)
  		{
  			arr[j]=false;
		}
	}
  }
  for(int i=2;i<=n;i++)
  {
  	if(arr[i]==true)
  		cout<<i<<endl;
  }
}
 
			      
time complexity = O(n loglog(n)) 
			      where n is the size of array;
			      

# Reversal-of-directed-graph
Write an algorithm that computes the reversal of a directed graph. For example, if a graph consists of A -> B -> C, it should become A &lt;- B &lt;- C.

#include<bits/stdc++.h>
using namespace std;
//function to add an edge from vertex source to vertex dest
void addedge(vector<int>adj[], int src, int dest)
{
	adj[src].push_back(dest);
}
//function to print adjacency list of a graph
void displaygraph(vector<int>adj[], int v)
{
	for(int i=0;i<v;i++)
	{
		cout<<i<<"-->";
		for(int j=0;j<adj[i].size();j++)
			cout<<adj[i][j]<<" ";
		cout<<"\n";
	}
}
//function to get transpose of a graph taking adjacency list
void transposegraph(vector<int>adj[],vector<int>transpose[], int v)
{
	//traverse the adjacency list of given graph and for each edge (u, v) add an edge (v, u) in the transpose graph adjacency list 
	for(int i=0;i<v;i++)
		for(int j=0;j<adj[i].size();j++)
			addedge(transpose,adj[i][j],i);
}
int main()
{
	int v=5;
	vector<int>adj[v];
	addedge(adj,0,1);
	addedge(adj,0,4);
	addedge(adj,0,3);
	addedge(adj,2,0);
	addedge(adj,3,2);
	addedge(adj,4,1);
	addedge(adj,4,3);
	//find transpose of graph reprsented by adjacency list adj[]
	vector<int>transpose[v];
	transposegraph(adj, transpose, v);
	//displaying adjacency of transpose list
	displaygraph(transpose, v);
	return 0;
}
	

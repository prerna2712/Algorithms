# Persistent segment tree

## Example problem :

We have an array a1, a2, ..., an and at first q update queries and then u ask queries which you have to answer online.
Each update query gives you numbers p and v and asks you to increase ap by v.
Each ask query, gives you three numbers `i` and `x` and `y` and asks you to print the value of `ax + ax + 1 + ... + ay` after performing `i - th` query.

## Solution

Each update query, changes the value of `O(log(n))` nodes in the segment tree, so you should keep rest of nodes (not containing p) and create `log(n)` new nodes. Totally, you need to have `q.log(n)` nodes. So, you can not use normal segment's indexing, you should keep the index of children in the arrays L and R.

If you update a node, you should assign a new index to its interval (for i - th query).

You should keep an array `root[q]` which gives you the index of the interval of the `root ( [0, n) )` after performing each query and a number ir = 0 which is its index in the initial segment tree (ans of course, an array s[MAXNODES] which is the sum of elements in that node). Also you should have a NEXT_FREE_INDEX = 1 which is always the next free index for a node.

First of all, you need to build the initial segment tree :

(In these codes, all arrays and queries are 0-based)

```cpp 
void build(int id = ir,int l = 0,int r = n){
	if(r - l < 2){
		s[id] = a[l];
		return ;
	}
	int mid = (l+r)/2;
	L[id] = NEXT_FREE_INDEX ++;
	R[id] = NEXT_FREE_INDEX ++;
	build(L[id], l, mid);
	build(R[id], mid, r);
	s[id] = s[L[id]] + s[R[id]];
}
```
(So, we should call build() )

Update function : (its return value, is the index of the interval in the new version of segment tree and id is the index of old one)
```cpp
int upd(int p, int v,int id,int l = 0,int r = n){
	int ID =  NEXT_FREE_INDEX ++; // index of the node in new version of segment tree
	if(r - l < 2){
		s[ID] = (a[p] += v);
		return ID;
	}
	int mid = (l+r)/2;
	L[ID] = L[id], R[ID] = R[id]; // in case of not updating the interval of left child or right child
	if(p < mid)
		L[ID] = upd(p, v, L[ID], l, mid);
	else
		R[ID] = upd(p, v, R[ID], mid, r);
	return ID;
}
```
(For the first query (with index 0) we should run root[0] = upd(p,  v,  ir) and for the rest of them, for j - th query se should run root[j] = upd(p,  v,  root[j - 1]) )

Function for ask queries :
```cpp
int sum(int x,int y,int id,int l = 0,int r = n){
	if(x >= r or l >= y)	return 0;
	if(x <= l && r <= y)	return s[id];
	int mid = (l+r)/2;
	return sum(x, y, L[id], l, mid) +
	       sum(x, y, R[id], mid, r);
}
```
(So, we should print the value of sum(x, y, root[i]) )

Source: [CF Blog](https://codeforces.com/blog/entry/15729)
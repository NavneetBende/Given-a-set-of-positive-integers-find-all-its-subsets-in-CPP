# Given-a-set-of-positive-integers-find-all-its-subsets-in-CPP

Set of Positive integers, find all its subsets in C++
Today in this article we will discuss the program in which we are Given a set of positive integers, find all its subsets in C++ Programming language.

Set of Positive integers, find all its subsets in C++
Algorithm :
We will discuss the recursive solution to the problem.

Create a recursive function that takes the following parameters, input array, the current index, the output array, or current subset, if all the subsets need to be stored then a vector of the array is needed if the subsets need to be printed only then this space can be ignored.
if the current index is equal to the size of the array, then print the subset or output array or insert the output array into the vector of arrays (or vectors) and return.
There are exactly two choices for very index.
Ignore the current element and call the recursive function with the current subset and next index, i.e i + 1.
Insert the current element in the subset and call the recursive function with the current subset and next index, i.e i + 1.
Code in C++
Run
#include <bits/stdc++.h>
using namespace std;

void subsetsUtil(vector<int>& A, vector<vector<int> >& res,vector<int>& subset, int index)
{
    res.push_back(subset);
    for (int i = index; i < A.size(); i++) {
 
        subset.push_back(A[i]);
        subsetsUtil(A, res, subset, i + 1);
        subset.pop_back();
    }
 
    return;
}

vector<vector<int> > subsets(vector<int>& A)
{
    vector<int> subset;
    vector<vector<int> > res;
 
    int index = 0;
    subsetsUtil(A, res, subset, index);
 
    return res;
}
 
int main()
{
    vector<int> array = { 1, 2, 3 };

    vector<vector<int> > res = subsets(array);
 
    for (int i = 0; i < res.size(); i++) {
        for (int j = 0; j < res[i].size(); j++)
            cout << res[i][j] << " ";
        cout << endl;
    }
 
    return 0;
}
Output :
1 
1 2 
1 2 3 
1 3 
2 
2 3 
3 

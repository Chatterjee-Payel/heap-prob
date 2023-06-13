# heap-prob
Given an array Arr[] of size N and an integer K, you have to choose the first two minimum elements of the array and erase them, then insert the sum of these two elements in the array until all the elements are greater than or equal to K and find the number of such operations required.

Example 1:

Input:
N = 6, K = 6 
Arr[] = {1, 10, 12, 9, 2, 3}
Output: 2
Explanation: First we add (1 + 2), now the
new list becomes 3 10 12 9 3, then we add
(3 + 3), now the new list becomes 6 10 12 9,
Now all the elements in the list are greater
than 6. Hence the output is 2 i:e 2 operations
are required to do this. 


class Solution{
  public:
    int minOperations(int arr[], int n, int k) {
        // code here
        priority_queue<int,vector<int>,greater<int>>pq;
        for(int i=0;i<n;i++){
            pq.push(arr[i]);
        }
        int count=0;
        while(pq.size()>1 && pq.top()<k)
        {
            int val1=pq.top();
            pq.pop();
            int val2=pq.top();
            pq.pop();
            int val3=val1+val2;
            pq.push(val3);
            count++;
        }
        if(pq.top()<k)
        {
            return -1;
        }
        return count;        
    }
};

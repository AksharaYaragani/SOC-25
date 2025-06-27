My project is on Competitive Programming.<br>
In Week 1, we focused on the basics, working on problems related to arrays and binary search.<br>
1. 121. Best Time to Buy and Sell Stock<br>
2.https://leetcode.com/problems/merge-sorted-array/<br>
3.https://leetcode.com/problems/majority-element/<br>
Given an integer array arr[], finding the subarray which has the maximum possible sum<br>

Kadane's algorithm -O(n) Time <br>
static int maxSubarraySum(int[] arr) { <br>
        int res = arr[0]; <br>
        int maxEnding = arr[0];<br>
        for (int i = 1; i < arr.length; i++) { <br>
            maxEnding = Math.max(maxEnding + arr[i], arr[i]); <br>
            res = Math.max(res, maxEnding); <br>
        } <br>
        return res;<br>
    }<br>
    
Binary Search:<br>
Binary Search Algorithm is a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(log N). <br>
Divide the search space into two halves by finding the middle index "mid".<br>
Compare the middle element of the search space with the key. <br>
If the key is found at middle element, the process is terminated.<br>
If the key is not found at middle element, choose which half will be used as the next search space.<br>
If the key is smaller than the middle element, then the left side is used for next search.<br>
If the key is larger than the middle element, then the right side is used for next search.<br>

Two pointer approach:<br>
You're tasked with figuring out the pair of elements where arr[p] + arr[q] add up to a certain number. <br>
private static int[] twoSum(int[] arr, int target) {<br>
    Arrays.sort(arr); // Sorting is optional, based on the specific logic<br>
    int left = 0;<br>
    int right = arr.length - 1;<br>
    while(left < right) {<br>
        // logic to find the two numbers that add up to target<br>
    }<br>
}<br>
5.https://leetcode.com/problems/sqrtx/
6.https://leetcode.com/problems/search-in-rotated-sorted-array/
7. https://leetcode.com/problems/search-in-rotated-sorted-array-ii/
8. https://leetcode.com/problems/two-sum/
9. https://leetcode.com/problems/valid-palindrome/
10.https://leetcode.com/problems/is-subsequence/<br>
The solutions for these questions are there in Week1 folder.<br>

In Week-2 we covered Sorting and problems related:<br>

Selection sort -O(n2) Time and O(1) space <br>
First we find the smallest element and swap it with the first element. This way we get the 
smallest element at its correct position. Then we find the smallest among remaining 
elements (or second smallest) and swap it with the second element. We keep doing this until 
we get all elements moved to correct position. <br>
Code: <br>
  for (int i = 0; i < n - 1; i++) { <br>
  int min_idx = i; <br>
  for (int j = i + 1; j < n; j++) { <br>
  if (arr[j] < arr[min_idx]) { <br>
  min_idx = j; <br>
  } <br>
  } <br>
  int temp = arr[i]; <br>
  arr[i] = arr[min_idx]; <br>
  arr[min_idx] = temp; <br>

Bubble Sort - O(n2) Time and O(1) space : <br>
First, we will select the range of the unsorted array. For that, we will run a loop(say i) that 
will signify the last index of the selected range. The loop will run backward from index n-1 to 
0(where n = size of the array). The value i = n-1 means the range is from 0 to n-1, and 
similarly, i = n-2 means the range is from 0 to n-2, and so on. <br>
Within the loop, we will run another loop (say j, runs from 0 to i-1 though the range is from 
0 to i) to push the maximum element to the last index of the selected range, by repeatedly 
swapping adjacent elements. <br>
Basically, we will swap adjacent elements (if arr[j] > arr[j+1]) until the maximum element of 
the range reaches the end. <br>
for (int i = n - 1; i >= 0; i--) { <br>
for (int j = 0; j <= i - 1; j++) { <br>
if (arr[j] > arr[j + 1]) { <br>
int temp = arr[j]; <br>
arr[j] = arr[j + 1]; <br>
arr[j + 1] = temp; <br>
} <br>
} <br>
}<br>

Insertion sort - O(n2) Time and O(1) space : <br>
We start with the second element of the array as the first element is assumed to be sorted. <br>
Compare the second element with the first element if the second element is smaller then 
swap them. Move to the third element, compare it with the first two elements, and put it in 
its correct position .Repeat until the entire array is sorted. <br>
for (int i = 0; i <= n - 1; i++) { <br>
int j = i; <br>
while (j > 0 && arr[j - 1] > arr[j]) { <br>
int temp = arr[j - 1]; <br>
arr[j - 1] = arr[j]; <br>
arr[j] = temp; <br>
j--; <br>
} <br>
}<br>

Merge sort - O ( nlogn) time and O(n) space : <br>
Merge sort follows the divide-and-conquer approach. It works by recursively dividing the 
input array into two halves, recursively sorting the two halves and finally merging them back 
together to obtain the sorted array. <br>
private static void merge(int[] arr, int low, int mid, int high) { <br>
        ArrayList<Integer> temp = new ArrayList<>(); // temporary array<br> 
        int left = low;      // starting index of left half of arr <br>
        int right = mid + 1;   // starting index of right half of arr <br>
        while (left <= mid && right <= high) { <br>
            if (arr[left] <= arr[right]) { <br>
                temp.add(arr[left]); <br>
                left++; <br>
            } else { <br>
                temp.add(arr[right]);<br> 
                right++; <br>
            } <br>
        } <br>
        while (left <= mid) { <br>
            temp.add(arr[left]); <br>
            left++; <br>
        } <br>
        while (right <= high) { <br>
            temp.add(arr[right]); <br>
            right++; <br>
        } <br>
        for (int i = low; i <= high; i++) { <br>
            arr[i] = temp.get(i - low); <br>
        } <br>
    } <br>
    public static void mergeSort(int[] arr, int low, int high) { 
if (low >= high) return; 
int mid = (low + high) / 2 ; 
mergeSort(arr, low, mid);  // left half 
mergeSort(arr, mid + 1, high); // right half 
merge(arr, low, mid, high);  // merging sorted halves 
}

Quick sort- O ( nlogn) time and O(n) space : <br>
Quick Sort is a divide-and-conquer algorithm like the Merge sort. But unlike Merge sort, this 
algorithm does not use any extra array for sorting. <br>
This algorithm is basically a repetition of two simple steps that are the following: <br>
• Pick a pivot and place it in its correct place in the sorted array. 
• Shift smaller elements(i.e. Smaller than the pivot) on the left of the pivot and larger 
ones to the right. <br>
static int partition(int[] arr, int low, int high) { 
int pivot = arr[high]; 
int i = low - 1; 
for (int j = low; j <= high - 1; j++) { 
if (arr[j] < pivot) { 
i++; 
swap(arr, i, j); 
} 
} 
swap(arr, i + 1, high);   
return i + 1; 
} 
static void swap(int[] arr, int i, int j) { 
int temp = arr[i]; 
arr[i] = arr[j]; 
arr[j] = temp; 
} 
static void quickSort(int[] arr, int low, int high) { 
if (low < high) { 
int pi = partition(arr, low, high); 
quickSort(arr, low, pi - 1); 
quickSort(arr, pi + 1, high); 
} 
}<br>

2. https://leetcode.com/problems/intersection-of-two-arrays/
3. https://leetcode.com/problems/kth-largest-element-in-a-stream/
4. https://leetcode.com/problems/largest-perimeter-triangle/
5. https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/
6. https://leetcode.com/problems/majority-element-ii/
7. https://leetcode.com/problems/kth-largest-element-in-an-array/
8. https://leetcode.com/problems/sort-colors/
9.https://leetcode.com/problems/3sum/<br>
Solutions for these questions are there in Week2 folder.<br>

Week 3: Divide and Conquer<br>
1.Given n intervals, find the total length of their union.
2.count no of inversions
https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1 
3.Search in a matrix
https://leetcode.com/problems/search-a-2d-matrix-ii/
4. Given n rectangular buildings in a 2-dimensional city, compute the area of all the buildings, eliminating hidden lines. The main task is to view buildings from a side and remove all sections that are not visible.All buildings share a common bottom and every building is represented by a triplet (left, ht, right).
5. minimum pages
https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1<br>

Binary tree and Binary search Tree:<br>
The tree is a non-linear data structure that stores data in the frm of a hierarchical structure. It is made up of a finite set of elements called nodes.<br>
In binary tree only if leftnode <root<right node . If it follows the order then it is BST. Whole left subtree and right subtree should also follow BST.<br>
 We learnt:Traversals,related problems<br>
 Preorder<br>
 Inorder<br>
 postorder<br>
 Levelorder<br>
6.check for bst<br>
https://www.geeksforgeeks.org/problems/check-for-bst/1?page=1&category=Binary%20Search%20Tree&sortBy=submissions<br>
7. search in a bst<br>
https://leetcode.com/problems/search-in-a-binary-search-tree/<br>
8.insert into a bst<br>
https://leetcode.com/problems/insert-into-a-binary-search-tree/<br>
9.inorder traversal<br>
https://leetcode.com/problems/binary-tree-inorder-traversal/<br>
10.preorder traversal<br>
https://leetcode.com/problems/binary-tree-preorder-traversal/<br>
11.postorder traversal<br>
https://leetcode.com/problems/binary-tree-postorder-traversal/<br>
12.kth largest element in bst<br>
https://www.geeksforgeeks.org/problems/kth-largest-element-in-bst/1?page=1&category=Binary%20Search%20Tree&sortBy=submissions<br>
13.Convert Sorted array into binary search tree<br>
https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/<br>
14.sort list<br>
https://leetcode.com/problems/sort-list/<br>
15. construct quad tree<br>
https://leetcode.com/problems/construct-quad-tree/<br>
16. Balanced binary search tree<br>
https://leetcode.com/problems/balance-a-binary-search-tree/<br>
17. Given two binary strings that represent value of two integers, find the product of two strings in decimal representation.<br>
 Solutions for these questions are there in Week3 folder.<br>
 
Week 4: Graphs:<br>
A Graph is a non-linear data structure that consists of vertices (nodes) and edges.
Adjacency Matrix Graph Representation:<br>
The Adjacency Matrix is a 2D array (matrix) where each cell on index (i,j) stores information about the edge from vertex i to vertex j.
Graphs Traversal : To traverse a Graph means to start in one vertex, and go along the edges to visit other vertices until all vertices, or as many as possible, have been visited.<br>
The two most common ways a Graph can be traversed are:<br>
Depth First Search (DFS)<br>
Breadth First Search (BFS)<br>
1.DFS<br>
2.BFS<br>
3.Print adjacency list<br>
4.Count connected components<br>
https://neetcode.io/problems/count-connected-components<br>
5.Number of Islands<br>
https://leetcode.com/problems/number-of-islands/<br>
6.1 Detect Cycles in 2D Grid<br>
https://leetcode.com/problems/detect-cycles-in-2d-grid/<br>
6.2 Undirected graph cycle<br>
https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1<br>
6.3 Directed Graph cycle<br>
https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1?page=1&category=Graph&sortBy=submissions<br>
7.Topological Sort<br>
https://www.geeksforgeeks.org/problems/topological-sort/1<br>
8. Flood fill<br>
https://www.geeksforgeeks.org/problems/flood-fill-algorithm1856/1<br>
9.Rotten Oranges<br>
https://www.geeksforgeeks.org/problems/rotten-oranges2536/1<br>
10.Course Schedule<br>
https://www.geeksforgeeks.org/problems/course-schedule/1<br>
11. Snake and Ladder Problem<br>
https://www.geeksforgeeks.org/problems/snake-and-ladder-problem4816/1<br>
12.Count possible paths<br>
https://www.geeksforgeeks.org/problems/possible-paths-between-2-vertices-1587115620/1<br>
Solutions to these questions are there in Week4 folder<br>

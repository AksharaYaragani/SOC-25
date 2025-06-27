My project is on Competitive Programming.<br>
In Week 1, we focused on the basics, working on problems related to arrays and binary search.<br>
1. 121. Best Time to Buy and Sell Stock<br>
2.https://leetcode.com/problems/merge-sorted-array/<br>
3.https://leetcode.com/problems/majority-element/<br>
Given an integer array arr[], finding the subarray which has the maximum possible sum<br>

Kadane's algorithm -O(n) Time <br>
static int maxSubarraySum(int[] arr) { <br>
        int res = arr[0]; <br>
        int maxEnding = arr[0];
        for (int i = 1; i < arr.length; i++) {
            maxEnding = Math.max(maxEnding + arr[i], arr[i]);
            res = Math.max(res, maxEnding);
        }
        return res;
    }
    
Binary Search:
Binary Search Algorithm is a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(log N). 
Divide the search space into two halves by finding the middle index "mid".
Compare the middle element of the search space with the key. 
If the key is found at middle element, the process is terminated.
If the key is not found at middle element, choose which half will be used as the next search space.
If the key is smaller than the middle element, then the left side is used for next search.
If the key is larger than the middle element, then the right side is used for next search.

Two pointer approach:
You're tasked with figuring out the pair of elements where arr[p] + arr[q] add up to a certain number. 
private static int[] twoSum(int[] arr, int target) {
    Arrays.sort(arr); // Sorting is optional, based on the specific logic
    int left = 0;
    int right = arr.length - 1;
    while(left < right) {
        // logic to find the two numbers that add up to target
    }
}
5.https://leetcode.com/problems/sqrtx/
6.https://leetcode.com/problems/search-in-rotated-sorted-array/
7. https://leetcode.com/problems/search-in-rotated-sorted-array-ii/
8. https://leetcode.com/problems/two-sum/
9. https://leetcode.com/problems/valid-palindrome/
10.https://leetcode.com/problems/is-subsequence/
The solutions for these questions are there in Week1 folder.

In Week-2 we covered Sorting and problems related:

Selection sort -O(n2) Time and O(1) space 
First we find the smallest element and swap it with the first element. This way we get the 
smallest element at its correct position. Then we find the smallest among remaining 
elements (or second smallest) and swap it with the second element. We keep doing this until 
we get all elements moved to correct position. 
Code: 
  for (int i = 0; i < n - 1; i++) { 
  int min_idx = i; 
  for (int j = i + 1; j < n; j++) { 
  if (arr[j] < arr[min_idx]) { 
  min_idx = j; 
  } 
  } 
  int temp = arr[i]; 
  arr[i] = arr[min_idx]; 
  arr[min_idx] = temp; 

Bubble Sort - O(n2) Time and O(1) space : 
First, we will select the range of the unsorted array. For that, we will run a loop(say i) that 
will signify the last index of the selected range. The loop will run backward from index n-1 to 
0(where n = size of the array). The value i = n-1 means the range is from 0 to n-1, and 
similarly, i = n-2 means the range is from 0 to n-2, and so on. 
Within the loop, we will run another loop (say j, runs from 0 to i-1 though the range is from 
0 to i) to push the maximum element to the last index of the selected range, by repeatedly 
swapping adjacent elements. 
Basically, we will swap adjacent elements (if arr[j] > arr[j+1]) until the maximum element of 
the range reaches the end. 
for (int i = n - 1; i >= 0; i--) { 
for (int j = 0; j <= i - 1; j++) { 
if (arr[j] > arr[j + 1]) { 
int temp = arr[j]; 
arr[j] = arr[j + 1]; 
arr[j + 1] = temp; 
} 
} 
}

Insertion sort - O(n2) Time and O(1) space : 
We start with the second element of the array as the first element is assumed to be sorted. 
Compare the second element with the first element if the second element is smaller then 
swap them. Move to the third element, compare it with the first two elements, and put it in 
its correct position .Repeat until the entire array is sorted. 
for (int i = 0; i <= n - 1; i++) { 
int j = i; 
while (j > 0 && arr[j - 1] > arr[j]) { 
int temp = arr[j - 1]; 
arr[j - 1] = arr[j]; 
arr[j] = temp; 
j--; 
} 
}

Merge sort - O ( nlogn) time and O(n) space : 
Merge sort follows the divide-and-conquer approach. It works by recursively dividing the 
input array into two halves, recursively sorting the two halves and finally merging them back 
together to obtain the sorted array. 
private static void merge(int[] arr, int low, int mid, int high) { 
        ArrayList<Integer> temp = new ArrayList<>(); // temporary array 
        int left = low;      // starting index of left half of arr 
        int right = mid + 1;   // starting index of right half of arr 
        while (left <= mid && right <= high) { 
            if (arr[left] <= arr[right]) { 
                temp.add(arr[left]); 
                left++; 
            } else { 
                temp.add(arr[right]); 
                right++; 
            } 
        } 
        while (left <= mid) { 
            temp.add(arr[left]); 
            left++; 
        } 
        while (right <= high) { 
            temp.add(arr[right]); 
            right++; 
        } 
        for (int i = low; i <= high; i++) { 
            arr[i] = temp.get(i - low); 
        } 
    } 
    public static void mergeSort(int[] arr, int low, int high) { 
if (low >= high) return; 
int mid = (low + high) / 2 ; 
mergeSort(arr, low, mid);  // left half 
mergeSort(arr, mid + 1, high); // right half 
merge(arr, low, mid, high);  // merging sorted halves 
}

Quick sort- O ( nlogn) time and O(n) space : 
Quick Sort is a divide-and-conquer algorithm like the Merge sort. But unlike Merge sort, this 
algorithm does not use any extra array for sorting. 
This algorithm is basically a repetition of two simple steps that are the following: 
• Pick a pivot and place it in its correct place in the sorted array. 
• Shift smaller elements(i.e. Smaller than the pivot) on the left of the pivot and larger 
ones to the right. 
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
}

2. https://leetcode.com/problems/intersection-of-two-arrays/
3. https://leetcode.com/problems/kth-largest-element-in-a-stream/
4. https://leetcode.com/problems/largest-perimeter-triangle/
5. https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/
6. https://leetcode.com/problems/majority-element-ii/
7. https://leetcode.com/problems/kth-largest-element-in-an-array/
8. https://leetcode.com/problems/sort-colors/
9.https://leetcode.com/problems/3sum/
Solutions for these questions are there in Week2 folder.

Week 3: Divide and Conquer
1.Given n intervals, find the total length of their union.
2.count no of inversions
https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1 
3.Search in a matrix
https://leetcode.com/problems/search-a-2d-matrix-ii/
4. Given n rectangular buildings in a 2-dimensional city, compute the area of all the buildings, eliminating hidden lines. The main task is to view buildings from a side and remove all sections that are not visible.All buildings share a common bottom and every building is represented by a triplet (left, ht, right).
5. minimum pages
https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1

Binary tree and Binary search Tree:
The tree is a non-linear data structure that stores data in the frm of a hierarchical structure. It is made up of a finite set of elements called nodes.
In binary tree only if leftnode <root<right node . If it follows the order then it is BST. Whole left subtree and right subtree should also follow BST.
 We learnt:Traversals,related problems
 Preorder
 Inorder
 postorder
 Levelorder
6.check for bst
https://www.geeksforgeeks.org/problems/check-for-bst/1?page=1&category=Binary%20Search%20Tree&sortBy=submissions
7. search in a bst
https://leetcode.com/problems/search-in-a-binary-search-tree/
8.insert into a bst
https://leetcode.com/problems/insert-into-a-binary-search-tree/
9.inorder traversal
https://leetcode.com/problems/binary-tree-inorder-traversal/
10.preorder traversal
https://leetcode.com/problems/binary-tree-preorder-traversal/
11.postorder traversal
https://leetcode.com/problems/binary-tree-postorder-traversal/
12.kth largest element in bst
https://www.geeksforgeeks.org/problems/kth-largest-element-in-bst/1?page=1&category=Binary%20Search%20Tree&sortBy=submissions
13.Convert Sorted array into binary search tree
https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/
14.sort list
https://leetcode.com/problems/sort-list/
15. construct quad tree
https://leetcode.com/problems/construct-quad-tree/
16. Balanced binary search tree
https://leetcode.com/problems/balance-a-binary-search-tree/
17. Given two binary strings that represent value of two integers, find the product of two strings in decimal representation.
 Solutions for these questions are there in Week3 folder.
 
Week 4: Graphs:
A Graph is a non-linear data structure that consists of vertices (nodes) and edges.
Adjacency Matrix Graph Representation:
The Adjacency Matrix is a 2D array (matrix) where each cell on index (i,j) stores information about the edge from vertex i to vertex j.
Graphs Traversal : To traverse a Graph means to start in one vertex, and go along the edges to visit other vertices until all vertices, or as many as possible, have been visited.
The two most common ways a Graph can be traversed are:
Depth First Search (DFS)
Breadth First Search (BFS)
1.DFS
2.BFS
3.Print adjacency list
4.Count connected components
https://neetcode.io/problems/count-connected-components
5.Number of Islands
https://leetcode.com/problems/number-of-islands/
6.1 Detect Cycles in 2D Grid
https://leetcode.com/problems/detect-cycles-in-2d-grid/
6.2 Undirected graph cycle
https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1
6.3 Directed Graph cycle
https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1?page=1&category=Graph&sortBy=submissions
7.Topological Sort
https://www.geeksforgeeks.org/problems/topological-sort/1
8. Flood fill
https://www.geeksforgeeks.org/problems/flood-fill-algorithm1856/1
9.Rotten Oranges
https://www.geeksforgeeks.org/problems/rotten-oranges2536/1
10.Course Schedule
https://www.geeksforgeeks.org/problems/course-schedule/1
11. Snake and Ladder Problem
https://www.geeksforgeeks.org/problems/snake-and-ladder-problem4816/1
12.Count possible paths
https://www.geeksforgeeks.org/problems/possible-paths-between-2-vertices-1587115620/1
Solutions to these questions are there in Week4 folder

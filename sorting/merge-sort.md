# Merge sort

Merge sort is a **Divide and Conquer algorithm**. The main idea is to create an auxiliary array, divide the original array into halves recursively, and compare each elements of these two arrays then put the smaller number to the auxiliary array. For each recursion, two sorts and one merge are executed. 

O\(nlogn\), **O\(n\)**

Python:

```text
# https://gist.github.com/mailpraveens/6261476
def merge(self, left_list, right_list):
    result = []
    i, j = 0, 0
    while i < len(left_list) and j < len(right_list):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result += left_list[i:] # loop may break before traversing all elements
    result += right_list[j:]
    return result

def mergesort(self, arr):
    if len(arr) <= 1:
        return arr
    middle = len(arr) // 2
    left = self.mergesort(arr[:middle])
    right = self.mergesort(arr[middle:])
    return self.merge(left, right) # left and right are functions
    
```

```text
class Solution:
    def __init__(self):
        self.result = []
        
    def sortIntegers(self, arr):
        if not arr or len(arr) == 0:
            return
        self.mergeSort(arr, 0, len(arr) - 1)
        
    def mergeSort(self, arr, start, end):
        if start < end:
            mid = (start + end) // 2
            self.mergeSort(arr, start, mid)
            self.mergeSort(arr, mid + 1, end)
            self.merge(arr, start, end)
    
    def merge(self, arr, start, end):
        mid = (start + end) // 2
        left = start
        right = mid + 1
        while left <= right and right <= end:
            if arr[left] < arr[right]:
                self.result.append(arr[left])
                left += 1
            else:
                self.result.append(arr[right])
                right += 1
        self.result += arr[left:right]
        self.result += arr[right:end+1]
        return self.result
```

Java:

```text
/* Java program for Merge Sort */
class MergeSort 
{ 
    // Merges two subarrays of arr[]. 
    // First subarray is arr[l..m] 
    // Second subarray is arr[m+1..r] 
    void merge(int arr[], int l, int m, int r) 
    { 
        // Find sizes of two subarrays to be merged 
        int n1 = m - l + 1; 
        int n2 = r - m; 
  
        /* Create temp arrays */
        int L[] = new int [n1]; 
        int R[] = new int [n2]; 
  
        /*Copy data to temp arrays*/
        for (int i=0; i<n1; ++i) 
            L[i] = arr[l + i]; 
        for (int j=0; j<n2; ++j) 
            R[j] = arr[m + 1+ j]; 
  
  
        /* Merge the temp arrays */
  
        // Initial indexes of first and second subarrays 
        int i = 0, j = 0; 
  
        // Initial index of merged subarry array 
        int k = l; 
        while (i < n1 && j < n2) 
        { 
            if (L[i] <= R[j]) 
            { 
                arr[k] = L[i]; 
                i++; 
            } 
            else
            { 
                arr[k] = R[j]; 
                j++; 
            } 
            k++; 
        } 
  
        /* Copy remaining elements of L[] if any */
        while (i < n1) 
        { 
            arr[k] = L[i]; 
            i++; 
            k++; 
        } 
  
        /* Copy remaining elements of R[] if any */
        while (j < n2) 
        { 
            arr[k] = R[j]; 
            j++; 
            k++; 
        } 
    } 
  
    // Main function that sorts arr[l..r] using 
    // merge() 
    void sort(int arr[], int l, int r) 
    { 
        if (l < r) 
        { 
            // Find the middle point 
            int m = (l+r)/2; 
  
            // Sort first and second halves 
            sort(arr, l, m); 
            sort(arr , m+1, r); 
  
            // Merge the sorted halves 
            merge(arr, l, m, r); 
        } 
    } 
```


# Binary Search
- It is a searching algorithm used for sorted or monotonic(strictly increasing or decreasing) search spaces
- It divides the space repeatedly to find the answer
### Internal working
- Divide the search space into two halves, by finding the mid
- compare mid with key if they are equal, the search is terminated
- if the key is not in the mid, chose which halve to search
  - if key is less than mid, then search the left side
  - if key is more than mid, then search the right side
- Above steps is continued until the key is found or search space is exhausted
### Time Complexity
- `O(logn)`
### Space Complexity
- `O(logn)`
### Code
#### Iterative
```
static int binarySearch(int arr[], int x) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            // Check if x is present at mid
            if (arr[mid] == x)
                return mid;

            // If x greater, ignore left half
            if (arr[mid] < x)
                low = mid + 1;

            // If x is smaller, ignore right half
            else
                high = mid - 1;
        }

        // If we reach here, then element was
        // not present
        return -1;
    }
```
#### Recursive
```
static int binarySearch(int arr[], int low, int high, int x) {
        if (high >= low) {
            int mid = low + (high - low) / 2;

            // If the element is present at the
            // middle itself
            if (arr[mid] == x)
                return mid;

            // If element is smaller than mid, then
            // it can only be present in left subarray
            if (arr[mid] > x)
                return binarySearch(arr, low, mid - 1, x);

            // Else the element can only be present
            // in right subarray
            return binarySearch(arr, mid + 1, high, x);
        }

        // We reach here when element is not present
        // in array
        return -1;
    }
```
### Real World Applications
- Searching in sorted array
- Finding first/last occurrence or closest match in sorted array
- In version control, git bisect use binary search to isolate faulty commits
### References
- [Binary Search](https://www.geeksforgeeks.org/dsa/binary-search/)
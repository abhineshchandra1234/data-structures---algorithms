# Sliding Window
- It is used to solve problems involving subarray or substring or window
- Instead of iterating over same elements, it maintains a range or window that moves step by step over the data, updating results incrementally
- It uses result of the previous window to calculate next window
### Types
#### Fixed Size
- Calculate result of first window, include k elements into it
- Then slide window by 1 and keep calculating result window by window
#### Variable Size
- we increase right pointer ie expand the window, until our condition is true
- if the condition doesnt match we shrink the window by increasing left pointer
- Again we increase the right pointer if the condition match
- we keep doing above steps till we reach the end of the array
### Time Complexity
- `O(n)`
### Problems
- Find maximum/minimum subarray, substring which satisfy specific conditions
- The size of subarray, substring `K` will be given
- These problems can be easily solved in `O(n^2)` using nested loop, but we use sliding window to solve it in `O(n)`
### References
- [Sliding Window Technique](https://www.geeksforgeeks.org/dsa/window-sliding-technique/)
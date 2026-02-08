# Recursion
- It is a process in which a function call itself directly or indirectly and this function is called recursive function
- Certain problems can be solved easily using recursion. like - tower of hanoi, preorder/inorder/postorder tree traversals, DFS of graph etc.
- Both recursive and iterative programs have same processing power. Every recursive problem can be written iteratively and vice versa
### Base Condition
- In recursion solution to the base case is provided, and larger problem is expressed in terms of smaller solutions, till base case is reached
### Stack Overflow Error
- If base condition is not reached or is not defined, then stack overflow error occurs
- In this case,the memory is exhausted by the function on the stack
### Memory Allocation
- when a function is called on main(), the memory is allocated to it on stack
- when a function calls itself, the memory of called function is allocated on top of calling function, and a different copy of
  each variable is created for each function call.
- When base case is reached the function return its value to the calling function and memory is de-allocated, and this process continues
### Advantages
- Provides a clean and simple way to write code
### Disadvantages
- Compared to iterative it requires more space and time
- All functions remain in stack until base case is reached
- function calls and overheads take more time 
### References
- [Recursion in Java](https://www.geeksforgeeks.org/java/recursion-in-java/)
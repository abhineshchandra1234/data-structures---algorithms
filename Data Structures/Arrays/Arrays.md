# Arrays
### Arrays
- It has a fixed size
- It stores data of same type
- we cannot insert or delete elements in the array
- We can access elements in `O(1)`
- We can change elements by assigning new value
- `ArrayIndexOutOfBoundsException` is thrown when we try to access out of bounds index
- we can create array of primitive types like - int, char, boolean etc or objects like - String, Integer or user-defined class objects etc. 
```
// Initialization
int[] arr = {5,6,1,2,7,9};
int[] arr = new int[size];

int[][] arr = {{1,2,3}, {4,5,6}, {7,8,9}};
int[][] arr = new int[5][6];
```
### Methods
- Arrays are object in java and inherit from Object class
- Like other objects, we can invoke methods like - `toString(), equals() and hashCode()` of Object class
- It has built in `length` property

### References
- [Arrays in Java](https://www.geeksforgeeks.org/java/arrays-in-java/)
### 1. Problem
  The method is given an array of integers and integer target.
  I need to return index of number which is equal to target, if there is no such number in array, the method should return -1; 

### 2. Approach
  My first solution was to just compare each element of array in for loop from 0 to nums.length, but it was O(n) complexity.
  I needed to find solution where each iteration would decrease numbers of iterations twice to get O(logn).
  I used binary search for this. I declared 3 variables: left, right, mid. while left less than right, each iteration I calculate mid: (right - left) divided by 2. 
  If element with index mid is less than target, I cut all elements with index less than mid. If element is bigger than target, cut all elements with index bigger than mid.
  If target element not found, we leave loop and return -1.

### 3. Time Complexity
  Each iteration we get rid of half of input array, if nums.length == n, each time n / 2, or logn with base = 2. Complexity = O(logn)

### 4. Space complexity
  We didn't create any copy of array or any new dynamic objects like map,
  only right, left constant variables + mid variable which we override each iteration. So complexity = O(1). 

### 5. Reflection / Improvement
  I don't see any better solutions, Even java.util.Arrays.binarySearch() method use similiar approach.
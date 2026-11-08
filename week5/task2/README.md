README Report: Sort an Array

1. Problem

I get an array of integers. I need to sort it in ascending order and return it. I must not use built-in sort functions.

2. Approach

I use merge sort.

- If the part of the array has 0 or 1 element, it is already sorted.
- Otherwise, I split the part in two halves and sort each half with the same method (recursion).
- Then I merge the two sorted halves. I use two pointers, one in each half, and I always copy the smaller element to a temporary array. When one half ends, I copy the rest of the other half.
- At the end I copy the merged part back to the original array.

Example: 5, 2, 3, 1
- Split: 5, 2 and 3, 1.
- Split again: 5, 2, 3, 1. Each one is a single element.
- Merge 5 and 2: 2, 5.
- Merge 3 and 1: 1, 3.
- Merge 2, 5 and 1, 3: compare 2 and 1, take 1. Compare 2 and 3, take 2. Compare 5 and 3, take 3. Then take 5.

Result: 1, 2, 3, 5

3. Time Complexity

Time Complexity: O(n log n)

I split the array in half each time, so there are about log n levels. On each level, merging looks at all n elements together, which is O(n) work. So the total is n times log n. I also use a temporary array of size n, so extra memory is O(n).

4. Reflection / Improvement

- Is there a more efficient approach? In time, no. O(n log n) is the best for sorting by comparing values. In memory, yes.
- What would I need to change? I would use heap sort. It sorts the array in place by building a heap and taking the biggest element again and again.
- What complexity could the improved solution achieve? O(n log n) time and O(1) extra memory, instead of O(n) memory for the temporary array.

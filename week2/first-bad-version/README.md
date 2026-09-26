### 1. Problem
  The method is given an integer `n` representing the total number of versions.
  I need to find and return the first bad version using the provided API `isBadVersion(version)`.

### 2. Approach
  A linear search checking versions from 1 to `n` would take $O(n)$ time complexity, which is too slow for large `n`.
  To optimize this to $O(\log n)$, I used binary search. I declared two variables: `left` initialized to 1 and `right` initialized to `n`.
  In each iteration while `left < right`, I calculate `mid` as `left + (right - left) / 2` to avoid integer overflow.
  If `isBadVersion(mid)` returns `true`, it means the first bad version is either `mid` or lies to its left, so I set `right = mid`.
  Otherwise, `mid` is still good, so the first bad version must be after `mid`, and I set `left = mid + 1`.
  When `left == right`, the loop terminates and `left` holds the index of the first bad version.

### 3. Time Complexity
  In each step of the binary search, the search space is halved ($n / 2$).
  Therefore, the time complexity is $O(\log n)$.

### 4. Space complexity
  The algorithm only uses a few primitive variables (`left`, `right`, `mid`) and does not allocate any extra data structures or call recursive stacks.
  Thus, the space complexity is $O(1)$.

### 5. Reflection / Improvement
  The solution is already optimal in terms of both time and space complexity.
  Using `left + (right - left) / 2` instead of `(left + right) / 2` prevents potential integer overflow issues when `n` is large.
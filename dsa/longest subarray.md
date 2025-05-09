twhat is a subarray?
{1,2,3,4,5} in this:
- {1,2} or{1,2,3} or {2,3} is a subarray
- contigious part of an array.
subsequence:
{1,2,3,4,5} = {1,2} or {1,3,5} 
- basically one which follows the order of the array



### First, how to find subarrays?
![[Pasted image 20250505205013.png]]
using two loops, for a starting index and an ending index


two ppointer approach:
```java
 while (right < n) {
            // if sum > k, reduce the subarray from left
            // until sum becomes less or equal to k:
            while (left <= right && sum > k) {
                sum -= a[left];
                left++;
            }

            // if sum = k, update the maxLen i.e. answer:
            if (sum == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }

            // Move forward thw right pointer:
            right++;
            if (right < n) sum += a[right];
        }

        return maxLen;
```




there is one hashing method, which we will skip for the time being.


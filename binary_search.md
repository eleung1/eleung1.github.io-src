---
layout: default
title: Binary Search
---

# Binary Search
Search algorithm which finds the target in a sorted array in O(log n).

## ELI5
For example, the number guessing game in which you have to guess the number I'm thinking of between 1-100.  You can continually guess the middle number, and narrow down the search space depending if I say higher/lower.

Say if you guess 50, and I say higher.  That means my number is between 51 - 100.  Next logical guess is the middle number between 51 - 100, which is 75.  If I say lower, that means my number is between 51 - 75.

Continue with guessing the middle number, until it's a match.

## Code
```
/**
 * Binary Search.
 *
 * @param nums Sorted ascending array of integers.
 * @param target The number we want to find
 * @return Index of the target if it exists in the array. Otherwise return -1
 */
public int binarySearch(int[] nums, int target) {

  // initialize low and high to bound of search area
  int low = 0;
  int high = nums.length - 1;

  // Keep comparing the mid num in our ever-shrinking search area
  // with target until we get a match
  while (low <= high) {

    // Find mid way point
    //int mid = ( low + high ) / 2;       // low + high could overflow if they're large
    int mid = low + ((high - low) / 2);   // To avoid overflow.  This yields the same result.

    if (nums[mid] < target) {
      // Middle num < target, search upper half
      low = mid + 1;
    } else if (nums[mid] > target) {
      // Middle num > target, search lower half
      high = mid - 1;
    } else {
      // Match!
      return mid;
    }
  }

  // If we reach this point, there is no match.
  return -1;
}
```
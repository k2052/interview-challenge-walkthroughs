# Frog River One

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Description](#description)
- [Manual Solution](#manual-solution)
- [Solution](#solution)

<!-- /TOC -->

Source: https://codility.com/programmers/task/frog_river_one

This is a walkthrough for the frog river crossing problem.

    A small frog wants to get to the other side of a river. The frog is currently located at position 0, and wants to get to position X. Leaves fall from a tree onto the surface of the river.

    You are given a non-empty zero-indexed array A consisting of N integers representing the falling leaves. A[K] represents the position where one leaf falls at time K, measured in seconds.

    The goal is to find the earliest time when the frog can jump to the other side of the river. The frog can cross only when leaves appear at every position across the river from 1 to X. You may assume that the speed of the current in the river is negligibly small, i.e. the leaves do not change their positions once they fall in the river.

    For example, you are given integer X = 5 and array A such that:

      A[0] = 1
      A[1] = 3
      A[2] = 1
      A[3] = 4
      A[4] = 2
      A[5] = 3
      A[6] = 5
      A[7] = 4
    In second 6, a leaf falls into position 5. This is the earliest time when leaves appear in every position across the river.

    Write a function:

    def solution(x, a)

    that, given a non-empty zero-indexed array A consisting of N integers and integer X, returns the earliest time when the frog can jump to the other side of the river.

    If the frog is never able to jump to the other side of the river, the function should return −1.

    For example, given X = 5 and array A such that:

      A[0] = 1
      A[1] = 3
      A[2] = 1
      A[3] = 4
      A[4] = 2
      A[5] = 3
      A[6] = 5
      A[7] = 4
    the function should return 6, as explained above.

    Assume that:

    N and X are integers within the range [1..100,000];
    each element of array A is an integer within the range [1..X].

    Complexity:

    expected worst-case time complexity is O(N);
    expected worst-case space complexity is O(X), beyond input storage (not counting the storage required for input arguments).

    Elements of input arrays can be modified.

## Description

You have an unordered stack of numbers to go through. You can only cross the river when you have counted numbers in a sequence up to a specified number. To cross you must know where you stopped counting.

For example, if you had the following numbers [1, 3, 1, 4, 2, 3, 5, 4] and you were counting to five, then six (your stack of numbers is zero indexed) would be the answer to cross the river.

## Manual Solution

```ruby
x = 5
a = [1, 3, 1, 4, 2, 3, 5, 4]
```

Look through numbers `a` until every number up to and including 5 `x` has appeared.
when this happens record where the number was and use that position to cross the river.

## Solution

```ruby
require 'set'
def solution(x, a)
  seen = Set.new
  a.each_with_index do |value, index|
    seen << value
    if seen.length == x
      return index
    end
  end

  return -1
end
```

Results: https://codility.com/demo/results/training3QJ39T-N2M/

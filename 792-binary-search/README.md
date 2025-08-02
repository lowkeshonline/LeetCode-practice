<h2><a href="https://leetcode.com/problems/binary-search">Binary Search</a></h2> <img src='https://img.shields.io/badge/Difficulty-Easy-brightgreen' alt='Difficulty: Easy' /><hr><p>Given an array of integers <code>nums</code> which is sorted in ascending order, and an integer <code>target</code>, write a function to search <code>target</code> in <code>nums</code>. If <code>target</code> exists, then return its index. Otherwise, return <code>-1</code>.</p>

<p>You must write an algorithm with <code>O(log n)</code> runtime complexity.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,0,3,5,9,12], target = 9
<strong>Output:</strong> 4
<strong>Explanation:</strong> 9 exists in nums and its index is 4
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,0,3,5,9,12], target = 2
<strong>Output:</strong> -1
<strong>Explanation:</strong> 2 does not exist in nums so return -1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt; nums[i], target &lt; 10<sup>4</sup></code></li>
	<li>All the integers in <code>nums</code> are <strong>unique</strong>.</li>
	<li><code>nums</code> is sorted in ascending order.</li>
</ul>

<h2>How to Approach</h2>

- Binary search **only works** on a **sorted array**.
- At each step, you cut the array in half by looking at the **middle**.

You have a sorted array:

```java
[2, 5, 8, 12, 16, 23, 38]
```

Lets say our target is 16.

We have to find the target index and return

now we have,

```java
start = 0
end = 6
mid = (0 + 6) / 2 = 3
arr[mid] = 12
```

- Since we got the mid index 3  is 12
- Check if the mid value is equal / greater / smaller than target
- If the target element == arr[mid] Return the mid index
- if target element < arr[mid] shrink search area specific to  left half of mid
- If target element > arr[mid] shrink search area specific to right half of mid
- Repeat these steps until the target == arr[mid]

### Dry Run

Iteration - 1:

```markdown
[2, 5, 8, 12, 16, 23, 38]

start = 0
end = 6
mid = (0 + 6) / 2 = 3 ==> [12]
arr[mid] = 12

target [16] == arr[mid] ==> 16 == 12 ==> NO
target [16] > arr[mid]  ==> 16 > 12 ==> YES

//So target would be on right half

start = mid + 1

//Now the array would be 

[16, 23, 38]
```

Iteration - 2:

```markdown
[16, 23, 38]

start = 4
end = 6
mid = 4 + 6 / 2 => 10 / 2 => 5
arr[mid] = 23

target [16] == arr[mid] ==> 16 == 23 ==> NO
target [16] > arr[mid]  ==> 16 > 23 ==> NO
target [16] < arr[mid]  ==> 16 < 23 ==> YES

//So the target would be on the left half

end = mid - 1;

//Now the array would be

[16]
```

Iteration - 3:

```markdown
[16]

start = 4
end = 4
mid = 4 + 4 / 2 => 8 / 2 => 4
arr[mid] = 16

target [16] == arr[mid] ==> 16 == 16 ==> 16

//So the target is found

since we have to return the index but not the value.

Return mid
```

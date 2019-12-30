# Rotate Array

Given an array, rotate the array to the right by k steps, where k is non-negative.

```
Example 1:

Input: [1,2,3,4,5,6,7] and k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

Example 2:

Input: [-1,-100,3,99] and k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

### Implementation 1 : Runtime = (kn) , Space = O(1)

```java
import java.util.Arrays;

public class App {

	public static void main(String[] args) {
		int[] input = {1, 2, 3, 4, 5, 6, 7};
		rotate(input, 3);
		System.out.println(Arrays.toString(input));
	}

	public static void rotate(int[] nums, int k) {
		for(int i = 1; i<= k; i++) {
			rotateArrayByOne(nums);
		}
	}

	public static void rotateArrayByOne(int[] nums) {
		int last = nums[nums.length-1];
		for(int i = nums.length-2; i >= 0; i--) {
			nums[i+1] = nums[i];
		}
		nums[0] = last;
	}
}
```
Above implementation have Runtime complexity of O(kn) and space complexity of O(1)

```
Runtime Complexity = O(kn)
Space Complexity   = O(1)
```

### Implementation 2 : Runtime = (n) , Space = O(k)

```java
public class App {

	public static void main(String[] args) {
		int[] input = {1, 2};
		rotate(input, 3);
		System.out.println(Arrays.toString(input));
	}

	public static void rotate(int[] nums, int k) {
		k %= nums.length;
		int length = nums.length;
		int[] temp = new int[k];
		for(int i = 0; i < k; i++) {
			temp[i] = nums[length - k + i];
		}
		
		for(int i = length - k - 1; i >= 0; i--) {
			nums[i + k] = nums[i];
		}
		
		for(int i = 0; i < k; i++) {
			nums[i] = temp[i];
		}
	}
}
```

Above implementation have Runtime complexity of O(n) and space complexity of O(k)

```
Runtime Complexity = O(n)
Space Complexity   = O(k)
```

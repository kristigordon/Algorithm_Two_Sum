![image](https://user-images.githubusercontent.com/66803124/119274008-9bfc8800-bbc2-11eb-836a-1a18b9a831d8.png)


# Algorithm Two Sum

The Two Number Sum coding question might be one of the very first coding questions you will ever do. 


In this problem, we are taking an array of intergers, and trying to see what combimation equals the given target sum.

We then need to return these integers in any order.

In the event where there aren't two numbers that when summed equal the target number, return an empty array. 

An interger cannot be added to itself and there will be a maximum of one pair that equals the target sum. 


For example:

the input [1, 2, 3], 4

should give the output (0, 2)

An example of what your interviewer will give you as instructions:
```
Given an unsorted list of integers, find a pair which add up to a given value. Identify the indices of the values which sum to the target. These indices must be distinct (i.e. you can't use a value in the same position twice).
```


The steps we will take to get started are                                                   :
```
1. Take the array
2. Iterate through it
3. Take index 0 and add it seperately to each other item in the array while checking the sum against target number
4. If equal, return the pair in the empty array that was created 
5. If there is not a pair that when added equals the target number, retrun an empty array. 
```

We can start this solution with a Brute Force option.
```
Brute force approach
def two_sum_brute_force(arr, target):
    length = len(arr)
    for i in range(length - 1):
        for j in range(1, length):
            # print(i, j)
            if arr[i] + arr[j] == target:
                return i, j
    return None
```

Optimal space and time complexity is O(n) Time and O(n) Space - where n is the length of the array

There are many other options to solve this problem such as using a Binary Search or a Hash Table.

Python Instructor, Robin Andrews, goes in depth through these in his article here:

https://www.codementor.io/@info658/classic-python-interview-question-the-two-sum-problem-1aajub9joq

Another Example:

class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            print(index)
            for i in range(index + 1, len(nums)):
                twoSum = nums[index] + nums[i]
                print(twoSum)
            print()

Your input
[2,7,11,15]
9
stdout
0
9
13
17
()
1
18
22
()
2
26
()
3
()

Output
[]
Diff
Expected
[0,1]

if twoSum == target:
                    print(index, i)
Your input
[2,7,11,15]
9
stdout
0
(0, 1)
()
1
()
2
()
3
()

Output
[]
Diff
Expected
[0,1]

class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            for i in range(index + 1, len(nums)):
                twoSum = nums[index] + nums[i]
                if twoSum == target:
                    return index, i
Accepted
Runtime: 24 ms
Your input
[2,7,11,15]
9
Output
[0,1]
Diff
Expected
[0,1]

MORE OPTIMIZED SOLUTION:
So, if we fix one of the numbers, say
x
, we have to scan the entire array to find the next number
y
which is
value - x
where value is the input parameter. Can we change our array somehow so that this search becomes faster?

class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            newTarget = target - nums[index]
            if newTarget in nums:
                print(newTarget)
Your input
[2,7,11,15]
9
stdout
7
2

Output
[]
Diff
Expected
[0,1]

print(nums.index(newTarget))

Your input
[2,7,11,15]
9
stdout
1
0

Output
[]
Diff
Expected
[0,1]


class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            newTarget = target - nums[index]
            if newTarget in nums:
                return index, nums.index(newTarget)
Accepted
Runtime: 16 ms
Your input
[2,7,11,15]
9
Output
[0,1]
Diff
Expected
[0,1]

Complexity Analysis
•	Time complexity : O(n^2)O(n2). For each element, we try to find its complement by looping through the rest of array which takes O(n)O(n) time. Therefore, the time complexity is O(n^2)O(n2).
•	Space complexity : O(1)O(1).



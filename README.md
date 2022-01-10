![image](https://user-images.githubusercontent.com/66803124/119274008-9bfc8800-bbc2-11eb-836a-1a18b9a831d8.png)


# Algorithm Two Sum

Whether you're using LeetCode, AlgoExpert, or just my site, the Two Number Sum coding question might be one of the very first coding questions you will ever do. This question takes you beyond the basics and introduces some logic and Big O Notation. If you haven't read my article explaining Big O Notation, you can definitely continue through this article. I'll link the deep dive so you can then directly apply what you learn here.  

Well. Let's get into it. In this problem, we are taking an array of intergers, and trying to see what combimation equals the given target sum.

We will then need to return these integers in any order.

In the event where there aren't two numbers that when summed equal the target number, return an empty array. 

An interger cannot be added to itself and there will be a maximum of one pair that equals the target sum. 


For example:

the input [1, 2, 3],  with a target of 4

should give the output (0, 2)

An example of what your interviewer will give you as instructions:
```
Given an unsorted list of integers, find a pair which add up to a given value. Identify the indices of the values which sum to the target. These indices must be distinct (i.e. you can't use a value in the same position twice).
```


The steps we will take to get started are                                                   :
```
1. Take the array
2. Iterate through it
3. Take index 0 and add it seperately to each other item in the array while 
        checking the sum against target number
4. If equal, return the pair in the empty array that was created 
5. If there is not a pair that when added equals the target number, retrun an empty array. 
```

We can start this solution with a Brute Force option.

```
class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            for i in range(index + 1, len(nums)):
                twoSum = nums[index] + nums[i]
                print(twoSum)
            print()
```
```
Your input
[2,7,11,15]
9

You can see what is happening when we print:

0 (Starting at index 0)
9 (Add index 0 and 1 which is 2 and 7 = 9)
13 (Add index 0 and 2 which is 2 and 11 = 13)
17 (Add index 0 and 3 which is 2 and 15 = 17)
()
1 (Now moving onto index 1)
18 (Add index 1 and 2 which is 7 and 11 = 18)
22 (Add index 1 and 3 which is 7 and 15 = 22)
()
2 (Now moving onto index 2)
26 (Add index 2 and 3 which is 11 and 15 = 26)
()
3 (Now moving onto index 3, there is nothing left to add.)
()
```
This is good for laying down the foundation, but now we need to return a value. 

If we take the index and i, we will have the position of the number pair.

Let's return those now. 

# Final Solution:
```
class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            for i in range(index + 1, len(nums)):
                twoSum = nums[index] + nums[i]
                if twoSum == target:
                    return index, i
```
```
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
```
Great! Accepted. 

We were able to complete the problem but that is not all your interviewer will expect from you. 

There will usually be many ways to optimize a solution. Many interviewees will even start with a non-optimized solution so they can then move into a better solution and explain the differences in the logic. This allows you to show more mastery of the subject area. 

Let's try a new approach. 

# MORE OPTIMIZED SOLUTION:
Up until this point we were taking one index and adding it to the other indexes in order, all while checking the sum against the target number. 

Since we already know all the potential numbers and the target sum, there is a better way of solving this. 

Let's take our first index 0 and minus it from the target number. 

For our above example of:
[2,7,11,15]
9
We would take 2 and minus it from the target of 9. This would give us 7. 

Now we know the number that would complete the problem, we can search through the list for it. 

Fortunately for us, the very next index is 7. Since there can only be one pair, we are done! 

This is much more effecient than the original method and will involve significantly less steps. 

```
class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            newTarget = target - nums[index]
            if newTarget in nums:
                print(newTarget)
```
```
Your input
[2,7,11,15]
9
stdout
7
2
```
```
print(nums.index(newTarget))

Your input
[2,7,11,15]
9
stdout
1
0

Expected
[0,1]
```
```
class Solution(object):
    def twoSum(self, nums, target):
        for index in range(len(nums)):
            newTarget = target - nums[index]
            if newTarget in nums:
                return index, nums.index(newTarget)
```
Our first Runtime was 24 ms!
We are now at 16 ms. Great work!
```
Accepted
Runtime: 16 ms
Your input
[2,7,11,15]
9

Output
[0,1]

Expected
[0,1]
```
Complexity Analysis
•	Time complexity : O(n^2)O(n2). 
For each element, we try to find its complement by looping through the rest of array which takes O(n)O(n) time. Therefore, the time complexity is O(n^2)O(n2).
•	Space complexity : O(1)O(1).

Another option for solving this problem is listed below. 
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

Optimal space and time complexity is O(n) Time and O(n) Space - where n is the length of the array.

There are many other options to solve this problem such as using a Binary Search or a Hash Table.

Python Instructor, Robin Andrews, goes in depth through these in his article here:

https://www.codementor.io/@info658/classic-python-interview-question-the-two-sum-problem-1aajub9joq


Good luck!

-Kris

## 1. Find All Numbers Disappeared in an Array

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]

## Solutions

### Time: O(n) | Space: O(1)

    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)):
            newIdx= abs(nums[i])-1
            if(nums[newIdx]>0):
                nums[newIdx] *= -1
        res=[]
        #print (nums)
        for j in range (len(nums)):
            if (nums[j] > 0):
                res.append(j+1)
        return res

### Time: O(n) | Space: O(n)

    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        numsHash={}
        for i in range(len(nums)):
            if(nums[i] not in numsHash):
                numsHash[nums[i]]=1
        res=[]
        for i in range (1, len(nums)+1):
            if i not in numsHash:
                res.append(i)
        return res
 
## 2. Duplicate Zeros

Given a fixed length array arr of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written.

Do the above modifications to the input array in place, do not return anything from your function.

Input: [1,0,2,3,0,4,5,0]

Output: null

Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]

## Solution

### Time: O(n) | Space: O(1)

    def duplicateZeros(self, arr: List[int]) -> None:
        """
        Do not return anything, modify arr in-place instead.
        """
        pos_dups=0
        left=0
        n=len(arr)-1
        
        while(left<=n-pos_dups):
            if(arr[left]==0):
                if(left==n-pos_dups):
                    arr[n]=0
                    n-=1
                    #break
                else:
                    pos_dups+=1
            left+=1
            
        for i in range(n-pos_dups,-1,-1):
            if(arr[i]!=0):
                arr[i+pos_dups]=arr[i]
            else:
                arr[i+pos_dups]=0
                pos_dups-=1
                arr[i+pos_dups]=0

## 3. Merge Sorted Array

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:

The number of elements initialized in nums1 and nums2 are m and n respectively.

You may assume that nums1 has enough space (size that is equal to m + n) to hold additional elements from nums2.

Input:

nums1 = [1,2,3,0,0,0], m = 3

nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]

## Solution

### Time: O(n+m)

    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i=m-1
        j=n-1
        k=m+n-1
        while (i>=0 and j>=0):
            if(nums1[i]>nums2[j]):
                nums1[k]=nums1[i]
                i-=1
            else:
                nums1[k]=nums2[j]
                j-=1
            k-=1
        while(j>=0):
            nums1[k]=nums2[j]
            j-=1
            k-=1
            
## 4. Remove Element

Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Input:

Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.

It doesn't matter what you leave beyond the returned length.

## Solution

### Time: O(n) | Space: O(1)

    def removeElement(self, nums: List[int], val: int) -> int:
        start=0
        end = len(nums)
        
        while (start<end):
            if(nums[start]==val):
                nums[start]=nums[end-1]
                end-=1
            else:
                start+=1
                
        return end

## 5. Remove Duplicates from Sorted Array

Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Input:

Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.

## Solution

### Time: O(n) | Space: O(1)

    class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        j=1
        for i in range(1,len(nums)):
            if(nums[i]!=nums[j-1]):
                nums[j]=nums[i]
                j+=1
        return j

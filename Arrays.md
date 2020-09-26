## 1. Find All Numbers Disappeared in an Array

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]

## Solutions

### Time: O(n)
### Space: O(1)

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

### Time: O(n)
### Space: O(n)

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

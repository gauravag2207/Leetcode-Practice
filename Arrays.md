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


